<template>
  <section
    class="relative z-20 overflow-hidden bg-[#1a332d] pt-20 pb-12 lg:pt-[80px] lg:pb-[90px]"
  >
    <div class="container mx-auto">
      <div class="-mx-4 flex flex-wrap">
        <div class="w-full px-4">
          <div class="mx-auto mb-[40px] max-w-[520px] text-center lg:mb-16">
            <h2
              class="mb-4 text-3xl font-bold text-dark font-montserrat sm:text-[40px] sm:leading-[48px]"
            >
              FAQ's
            </h2>
          </div>
        </div>
      </div>
      <div class="w-full flex  justify-center">
      <div class="-mx-4 md:w-[80%] w-full flex justify-center">
        <div class="w-full px-4 flex flex-col font-montserrat  xxl:text[37px] text-[23px] max-sm:text-[23px] max-ssm:text-[21px] max-vsm:text-[21px] justify-center">
          <div v-for="faq in faqs" :key="faq.id" class="border-b-[1px] border-gray-500 py-2">
            <div
              class="w-full rounded-lg"
            >
              <button class="faq-btn flex relative w-full text-left" @click="handleToggle(faq.id)">
                <div
                  class="flex h-10 w-full relative -mt-[1.8px] max-w-[40px] items-center justify-center rounded-lg"
                >
                  <svg
                    class="fill-primary stroke-primary duration-200 ease-in-out"
                    :class="activeFaq == faq.id ? 'rotate-0':'-rotate-90'"
                    width="13"
                    height="10"
                    viewBox="0 0 17 10"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M7.28687 8.43257L7.28679 8.43265L7.29496 8.43985C7.62576 8.73124 8.02464 8.86001 8.41472 8.86001C8.83092 8.86001 9.22376 8.69083 9.53447 8.41713L9.53454 8.41721L9.54184 8.41052L15.7631 2.70784L15.7691 2.70231L15.7749 2.69659C16.0981 2.38028 16.1985 1.80579 15.7981 1.41393C15.4803 1.1028 14.9167 1.00854 14.5249 1.38489L8.41472 7.00806L2.29995 1.38063L2.29151 1.37286L2.28271 1.36548C1.93092 1.07036 1.38469 1.06804 1.03129 1.41393L1.01755 1.42738L1.00488 1.44184C0.69687 1.79355 0.695778 2.34549 1.0545 2.69659L1.05999 2.70196L1.06565 2.70717L7.28687 8.43257Z"
                      class="fill-gray-400 hover:fill-gray-300"
                      stroke=""
                    />
                  </svg>
                </div>

                <div class="w-full">
                  <h4 :class="activeFaq == faq.id?'text-gray-300':'text-gray-400'" class="mt-1 transition-all font-poppins  text-lg font-base text-gray-400 hover:text-gray-300">
                    {{ faq.header }}
                  </h4>
                </div>
              </button>

              <transition v-if="activeFaq === faq.id" name="fade" mode="out-in">
                <div v-if="activeFaq === faq.id" :class="[activeFaq === faq.id ? 'block' : 'hidden', 'transition-all duration-700']" class="pl-[62px]">
                  <p class="py-3 tracking-wide text-base leading-relaxed text-body-color text-dark-6">
                    {{ faq.text }}
                  </p>
                </div>
              </transition>
            </div>
          </div>
        </div>
        </div>
      </div>
    </div>

    
  </section>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  setup() {
    const header = '';
    const text = ``;
    const faqs = ref ([
    { id: 1, header:'What is raaga?', text :`RAAGA is a national level music festival organized by SWARA, the official music club of K L University. The music festival consists of several competitions, spot events and expos to celebrate music in different ways and to encourage people to participate in areas of their liking, symbolising that music is for everyone.`},
    { id: 2, header:'What are the events conducted in Raaga?', text :`Voice of raaga(Western/Classical vocal solo),Battle of bands,Solo instrumental(Percussion&Non percussion),Western group,Singing jodi.`},
    { id: 3, header:'Does Raaga events have Any cash prizes?', text :`Yes, you can find it in corresponding event guidelines and participation certificate   will also be provided to every participant.There will be momentos and medals will be provided for prize winners.`},
    { id: 4, header:'Can Outsiders,other than college students participate?', text :`Yes, they can register through our official website and participation.There will be transportation and lodging requirements provided if they pay the registration fee.`},  
    { id: 5, header:'Is there any rule that controversial songs to performed at the competitions?', text :`No, there isn't a specific rule banning controversial songs from being performed at competitions. However, organizers may have guidelines or restrictions in place to ensure that performances remain appropriate for the audience and venue.`},  
    ]);

    const activeFaq = ref(null);

    const handleToggle = (faqId) => {
      activeFaq.value = activeFaq.value === faqId ? null : faqId;
    };

    return {
      faqs,
      activeFaq,
      handleToggle,
    };
  },
};
</script>

<style scoped>

.fade-enter-active, .fade-leave-active {
  transition: all;
  transition-duration: 500ms;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
  transform: translateY(-20px); 
}
</style>
