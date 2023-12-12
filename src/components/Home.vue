<script>
import { ref, reactive, onBeforeMount, computed, onMounted, onUnmounted } from "vue";
import _ from 'underscore';
import gsap from 'gsap';

import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default{
  name: "Home",
  setup() {
    const triggers = ScrollTrigger.getAll();
    // 第一幕
    const txtzero = ref(null);
    const logo = ref(null);
    const logotxt= ref(null);
    const lineone =ref(null);
    // 第二幕
    const txtone = ref(null);
    const titleone = ref(null);
    // 第三幕
    const txttwo = ref(null);
    const titletwo = ref(null);
    // 第三幕
    const txtthree = ref(null);
    const titlethree = ref(null);
    // 邊角文字
    const topbgtxt = ref(null);
    const bgtxt = ref(null);
    // 上面
    const topl = ref(null);
    // 左邊
    const lefta = ref(null);
    const lefto = ref(null);
    const leftb = ref(null);
    const leftaa = ref(null);
    const leftn = ref(null);
    const leftg = ref(null);

    const leftc = ref(null);
    const leftr = ref(null);
    const lefte = ref(null);
    const leftaaa = ref(null);
    const leftt = ref(null);
    const lefti = ref(null);
    const leftv = ref(null);
    const leftii = ref(null);
    const lefttt = ref(null);
    const lefty = ref(null);
    // 右下
    const rightg = ref(null);
    const righta = ref(null);
    const righto = ref(null);

    const rightb = ref(null);
    const rightaa = ref(null);
    const rightn = ref(null);
    const rightgg = ref(null);

    const rightc = ref(null);
    const rightr = ref(null);
    const righte = ref(null);
    const rightaaa = ref(null);
    const rightt = ref(null);
    const righti = ref(null);
    const rightv = ref(null);
    const rightii = ref(null);
    const righttt = ref(null);
    const righty = ref(null);

    // 頁尾
    const Bottomdata = reactive({
      info : 'Copyright © 2023 GAO BANG CREATIVITY All Rights Reserved',
      year: new Date().getFullYear(),
      updatedInfo: computed(() => `Copyright © ${Bottomdata.year} GAO BANG CREATIVITY All Rights Reserved`)
    });

    const debounceFunc = (func, delay) => {
       let timer;
        return function(...args) {
           const context = this;
           clearTimeOut(timer);
           timer = setTimeOut(() => {
               func.apply(context, args);
           }, delay)
         }
    };
    function gsapSet() {
      ScrollTrigger.matchMedia({
        "(min-width: 368px)": () => {
          //
          gsap.from(logo.value, {
            y: 2000,
            opacity: 0,
            scale: 0,
            delay: 0.25,
            duration: 0.5,
          });
          gsap.to(logo.value, {
           scrollTrigger: {
            start: "top -80",
            end: "99999", 
            toggleClass: {
              className: 'logo-to', 
              targets: logo.value
            },
           },
           scale: 1
          });
          //
          gsap.from(logotxt.value, {
            y: 2000,
            opacity: 0,
            scale: 0,
            delay: 0.75,
            duration: 0.5,
          });
          gsap.to(logotxt.value, {
           scrollTrigger: {
            start: "top -10",
            end: "99999",
            toggleClass: {
              className: 'logotxt-to', 
              targets: logotxt.value
            },

           },
           scale: 1,
          });
          //
          gsap.set(topbgtxt.value, {
            opacity: 0,
          });

          gsap.to(topbgtxt.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=600px",
            end: "99999",
            scrub: true,
            toggleClass: "active",
            markers: false,
            toggleClass: {
              className: 'topbgtxt-to', 
              targets: topbgtxt.value
            },
           },
           // opacity:1,
          });
          //
          gsap.set(bgtxt.value, {
            opacity:0,
          });

          gsap.to(bgtxt.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=600px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity:1,
          });
          //
          gsap.set(titleone.value, {
            y: 300,
            opacity: 0,
            scale: 3,
          });

          gsap.to(titleone.value, {
           scrollTrigger: {
            trigger: txtzero.value,
            start: "top -30",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           onEnter() {
              async function play() {
                const sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

                // 過渡動畫的時間間隔和延遲時間
                const intervalTime = 1000;
                const delayTime = 2000;

                // 設定文字的初始狀態
                $('.center').removeClass('hidden');
                $('.blurtext span:nth-child(1)').addClass('active');

                // 使用防抖函數控制 play 函數的執行次數
                const debouncedPlay = _.debounce(play, delayTime + 2 * intervalTime);

                // 隱藏第一個單字，並等待 0.5 秒後執行下一步動作
                $('.t').addClass('hidden');
                await sleep(3500);

                // 過渡動畫
                for (let i = 1; i < $('.blurtext span').length; i++) {
                  // 移除透明濾鏡動畫
                  $('.blurtext span.past').removeClass('past');
                  // 新增 past class, 移除 active class
                  $('.blurtext span.active').addClass('past').removeClass('active');
                  // 新增 active class，清除濾鏡動畫
                  $('.blurtext span.past + span').addClass('active');

                  // 如果所有單字都已經過渡完成，則跳出迴圈
                  if ($('.blurtext span.active').length == 0) {
                    break;
                  }

                  // 等待一段時間後繼續下一步動作
                  await sleep(intervalTime);
                }

                // 隱藏第一個單字，並等待 2 秒後執行下一步動作
                $('.t').addClass('hidden');
                await sleep(delayTime);

                // 使用防抖函數來控制函數的執行次數
                debouncedPlay();
              }

              play();

          },
           y: 200,
           scale: 1,
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.from(lineone.value, {
            y: 200,
            opacity: 0,
            scale: 0,
            delay: 1,
            duration: 0.5,
          });
          gsap.to(lineone.value, {
           scrollTrigger: {
            start: "top -10",
            end: "99999",
            toggleClass: {
              className: 'line-to', 
              targets: lineone.value
            },
           },
           scale: 1,
          });
          //
          gsap.set(titletwo.value, {
            y: 40,
            filter: "blur(16px)",
            opacity: 0,
            scale: 3,
          });

          gsap.to(titletwo.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           y: 0,
           scale: 1,
           opacity: 1,
           filter: "blur(0px)",
           duration: 0.25,
          });
          //
          gsap.set(titlethree.value, {
            y: 40,
            filter: "blur(16px)",
            opacity: 0,
            scale: 3,
          });

          gsap.to(titlethree.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           y: 0,
           scale: 1,
           opacity: 1,
           filter: "blur(0px)",
           duration: 0.25,
          });
          // new left
          gsap.set(lefta.value, {
            opacity: 0.1,
          });

          gsap.to(lefta.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefto.value, {
            opacity: 0.1,
          });

          gsap.to(lefto.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftb.value, {
            opacity: 0.1,
          });

          gsap.to(leftb.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftaa.value, {
            opacity: 0.1,
          });

          gsap.to(leftaa.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftn.value, {
            opacity: 0.1,
          });

          gsap.to(leftn.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftg.value, {
            opacity: 0.1,
          });

          gsap.to(leftg.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftc.value, {
            opacity: 0.1,
          });

          gsap.to(leftc.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftr.value, {
            opacity: 0.1,
          });

          gsap.to(leftr.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefte.value, {
            opacity: 0.1,
          });

          gsap.to(lefte.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftaaa.value, {
            opacity: 0.1,
          });

          gsap.to(leftaaa.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftt.value, {
            opacity: 0.1,
          });

          gsap.to(leftt.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefti.value, {
            opacity: 0.1,
          });

          gsap.to(lefti.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftv.value, {
            opacity: 0.1,
          });

          gsap.to(leftv.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftii.value, {
            opacity: 0.1,
          });

          gsap.to(leftii.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefttt.value, {
            opacity: 0.1,
          });

          gsap.to(lefttt.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefty.value, {
            opacity: 0.1,
          });

          gsap.to(lefty.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          // new right
          gsap.set(rightg.value, {
            opacity: 0.1,
          });

          gsap.to(rightg.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righta.value, {
            opacity: 0.1,
          });

          gsap.to(righta.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righto.value, {
            opacity: 0.1,
          });

          gsap.to(righto.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightb.value, {
            opacity: 0.1,
          });

          gsap.to(rightb.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightaa.value, {
            opacity: 0.1,
          });

          gsap.to(rightaa.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightn.value, {
            opacity: 0.1,
          });

          gsap.to(rightn.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightgg.value, {
            opacity: 0.1,
          });

          gsap.to(rightgg.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightc.value, {
            opacity: 0.1,
          });

          gsap.to(rightc.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightr.value, {
            opacity: 0.1,
          });

          gsap.to(rightr.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righte.value, {
            opacity: 0.1,
          });

          gsap.to(righte.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightaaa.value, {
            opacity: 0.1,
          });

          gsap.to(rightaaa.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightt.value, {
            opacity: 0.1,
          });

          gsap.to(rightt.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righti.value, {
            opacity: 0.1,
          });

          gsap.to(righti.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightv.value, {
            opacity: 0.1,
          });

          gsap.to(rightv.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightii.value, {
            opacity: 0.1,
          });

          gsap.to(rightii.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righttt.value, {
            opacity: 0.1,
          });

          gsap.to(righttt.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righty.value, {
            opacity: 0.1,
          });

          gsap.to(righty.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
        },
      });
    };

    onMounted(() => {
      ScrollTrigger.refresh();
      gsapSet();
    });
    onUnmounted(() => {
      triggers.forEach((trigger) => {
        trigger.kill();
      });
      ScrollTrigger.clearMatchMedia();
    });
    return {
      // 第一幕
      txtzero,
      logo,
      logotxt,
      lineone,
      // 第二幕
      txtone,
      titleone,
      // 第三幕
      txttwo,
      titletwo,
      // 第四幕
      txtthree,
      titlethree,
      // 邊角文字
      topbgtxt,
      bgtxt,
      // 上面
      topl,
      // 左邊
      lefta,
      lefto,
      leftb,
      leftaa,
      leftn,
      leftg,

      leftc,
      leftr,
      lefte,
      leftaaa,
      leftt,
      lefti,
      leftv,
      leftii,
      lefttt,
      lefty,

      // 右下
      rightg,
      righta,
      righto,

      rightb,
      rightaa,
      rightn,
      rightgg,

      rightc,
      rightr,
      righte,
      rightaaa,
      rightt,
      righti,
      rightv,
      rightii,
      righttt,
      righty,
      // 頁尾
      Bottomdata
    }
  },
};
</script>
<template>
<div 
class="relative overflow-hidden" style="background: #E6B020;">
  <!--  -->
  <div ref="topbgtxt">
    <div 
    class="fixed top-[1rem] left-[1rem] sm:left-[2rem] flex flex-row text-[10px] sm:text-[18px] text-white z-40 tracking-[16px] sm:tracking-[36px] md:tracking-[28px] font-GenJyuuGothicBold">
        <span>G</span>
        <span ref="topl">A</span>
        <span ref="topl">O</span>
        <span ref="topl">B</span>
        <span ref="topl">A</span>
        <span ref="topl">N</span>
        <span ref="topl">G</span>
        <span ref="topl">R</span>
        <span ref="topl">E</span>
        <span ref="topl">A</span>
        <span ref="topl">T</span>
        <span ref="topl">I</span>
        <span ref="topl">V</span>
        <span ref="topl">I</span>
        <span ref="topl">T</span>
        <span ref="topl">Y</span>
    </div>
  </div>
  <div ref="bgtxt">
    <div 
    class="fixed top-[2.9rem] sm:top-[3.6rem] left-[1rem] sm:left-[2rem] flex flex-col text-[10px] sm:text-[18px] text-white z-40 font-GenJyuuGothicBold justify-center items-center">
        <span ref="lefta">A</span>
        <span ref="lefto" class="mt-[0.7rem] md:mt-[14px]">O</span>

        <span ref="leftb" class="mt-[0.7rem] md:mt-[14px]">B</span>
        <span ref="leftaa" class="mt-[0.7rem] md:mt-[14px]">A</span>
        <span ref="leftn" class="mt-[0.7rem] md:mt-[14px]">N</span>
        <span ref="leftg" class="mt-[0.7rem] md:mt-[14px]">G</span>

        <span ref="leftc" class="mt-[0.7rem] md:mt-[14px]">C</span>
        <span ref="leftr" class="mt-[0.7rem] md:mt-[14px]">R</span>
        <span ref="lefte" class="mt-[0.7rem] md:mt-[14px]">E</span>
        <span ref="leftaaa" class="mt-[0.7rem] md:mt-[14px]">A</span>
        <span ref="leftt" class="mt-[0.7rem] md:mt-[14px]">T</span>
        <span ref="lefti" class="mt-[0.7rem] md:mt-[14px]">I</span>
        <span ref="leftv" class="mt-[0.7rem] md:mt-[14px]">V</span>
        <span ref="leftii" class="mt-[0.7rem] md:mt-[14px]">I</span>
        <span ref="lefttt" class="mt-[0.7rem] md:mt-[14px]">T</span>
        <span ref="lefty" class="mt-[0.7rem] md:mt-[14px]">Y</span>

    </div>
    <div 
    class="fixed bottom-[3.5rem] sm:bottom-[1rem] right-[0rem] flex flex-col text-[10px] sm:text-[18px] text-white tracking-[18px] sm:tracking-[24px] z-40 font-GenJyuuGothicBold">
        <div class="flex flex-row justify-end">
          <span ref="rightg">G</span>
          <span ref="righta">A</span>
          <span ref="righto">O</span>
        </div>
        <div class="flex flex-row justify-end mt-[10px]">
          <span ref="rightb">B</span>
          <span ref="rightaa">A</span>
          <span ref="rightn">N</span>
          <span ref="rightgg">G</span>
        </div>
        <div class="flex flex-row justify-end mt-[10px]">
          <span ref="rightc">C</span>
          <span ref="rightr">R</span>
          <span ref="righte">E</span>
          <span ref="rightaaa">A</span>
          <span ref="rightt">T</span>
          <span ref="righti">I</span>
          <span ref="rightv">V</span>
          <span ref="rightii">I</span>
          <span ref="righttt">T</span>
          <span ref="righty">Y</span>
        </div>
    </div>
  </div>
  <!-- -->
  <!--  -->
  <div class="fixed left-[8px] lg:left-[450px] top-2 z-10 w-[600px] h-[600px] rounded-full blur-[200px] top_animate"></div>
  <div class="fixed right-8 bottom-8 z-10 w-[600px] h-[600px] rounded-full blur-[200px] right_animate"></div>
  <div class="fixed left-8 bottom-8 z-10 w-[600px] h-[600px] rounded-full blur-[200px] left_animate"></div>
  <!--  -->
  <section 
  ref="txtzero"
  class="w-full h-screen flex flex-col justify-center items-center">
    <img 
    ref="logo"
    src="/logo.svg" class="logo z-40">
    <h5 
    ref="logotxt"
    class="fixed flex justify-center items-center mt-[12rem] sm:mt-60 text-[1rem] sm:text-2xl md:text-[1.7rem] md:leading-10 text-white font-GenJyuuGothicBold tracking-[1px] sm:tracking-[1px] z-40" 
    style="text-indent: 0em;">GAO BANG CREATIVITY</h5>
    <span 
    ref="lineone"
    class="absolute left-[50%] divideline mt-[65vh] sm:mt-[580px] lg:mt-[500px] h-[60px] z-40"></span>

    <p 
    ref="titleone"
    class="absolute text-white text-center text-[1rem] sm:text-2xl md:text-[1rem] z-40 leading-[30px] pt-[30vh] px-8 sm:px-0 tracking-[1px]">
    <span class="flex flex-row justify-center">
    動漫IP策劃、活動企劃、行銷媒體 + <span class="t blurtext pl-[0.7rem] w-[100px] h-[10px] leading-[1.9rem]">創意</span><br>
    <div class="center hidden">
      <div class="blurtext pl-2">
        <span>創意</span>
        <span>科技</span>
        <span>創意</span>
        <span>科技</span>
        <span>創意</span>
        <span>科技</span>
        <span>創意</span>
      </div>
    </div>
    </span>
    Make dreams come true, make everything happen.
    </p>
  </section>

  <!--  -->
  <section 
  ref="txttwo"
  class="w-full h-screen flex flex-col justify-center items-center">
    <p 
    ref="titletwo"
    class="text-white text-center z-40 leading-[30px] tracking-[1px]">
    主題展覽、主題餐廳、主題活動、授權策劃
    <br>
    用動漫IP的魅力，打造快樂的使命</p>
  </section>
  <!--  -->
  <section 
  ref="txtthree"
  class="w-full h-screen flex justify-center items-center">
    <p 
    ref="titlethree"
    class="text-white text-center z-40 leading-[30px] tracking-[1px]">
    與你一起，用創意渲染快樂<br>
    Share＆Love Peace<br><br>
    <a href="mailto:pkbaby0707@gmail.com" class="underline z-40">contact us</a></p>
  </section>
  <!--  -->
  <footer 
  class="fixed bottom-5 w-full flex flex-col justify-center items-center">
    <div 
    class="flex flex-col justify-center items-center">
      <a 
      class="text-white text-[10px]" 
      href="mailto:pkbaby0707@gmail.com">{{ Bottomdata.updatedInfo }}</a>
    </div>
  </footer>
</div>
</template>
