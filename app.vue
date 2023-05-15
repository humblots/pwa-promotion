<template>
<div class="jumbotron fade-in">
    <h1>PWAs are<br><span class="highlighted-title">awesome</span></h1>
</div>
<div>
    <section>
        <p class="pop-in">🚀 Say goodbye to slow-loading websites and limited functionality! Introducing Progressive Web Apps (PWAs) – the cutting-edge solution that revolutionizes your online experience like never before. 🌟</p>
        <p class="pop-in">🌍 Seamlessly bridging the gap between native apps and traditional websites, PWAs are the future of web technology. 🌐 With just a tap or click, unlock a world of endless possibilities right from your browser!</p>
        <p class="pop-in">📈 Lightning-Fast Performance: Say farewell to frustrating loading times! PWAs leverage advanced caching techniques, delivering blazing-fast speeds even in low network conditions. Instantly access your favorite apps and content without delays, ensuring a seamless user experience.</p>
        <p class="pop-in">💡 Offline Functionality: No internet? No problem! PWAs are designed to work offline, offering uninterrupted access to essential features and content. Whether you're on a plane, subway, or remote location, you can still stay connected and productive with PWAs.</p>
        <p class="pop-in">🔒 Enhanced Security: Your digital safety is our top priority. PWAs employ secure HTTPS connections and are regularly updated to protect your data from potential threats. Rest easy knowing that your information is shielded within the robust architecture of PWAs.</p>
        <p class="pop-in">📱 Cross-Platform Compatibility: Embrace flexibility and convenience! PWAs are platform-agnostic, running smoothly across all devices and operating systems. Whether you're on your smartphone, tablet, or desktop, enjoy a consistent and immersive experience everywhere you go.</p>
        <p class="pop-in">And many more awesome features to <span class="highlighted-title">DISCOVER</span> !</p>
    </section>
    <section>
        <h2>How does it work ?</h2>
        <p>
            PWA uses the device's browser capabilities to install and run websites as if they were real applications. Therefore some limitations still exists as all browsers aren't compatible with PWAs.
            For example, PWA features are supported to varying degrees by Google Chrome, Apple Safari, Firefox for Android, and Microsoft Edge but not by Firefox for desktop.
        </p>
        <p>
            To install a PWA on your device, go to a website that respects the requirements of a PWA (HTTPS protocol, webmanifest and a service worker). From there, a pop up should appear if your device is eligible.
            On desktop a button should also appear at the navigation bar level.
        </p>
    </section>
    <section>
        <h2>Compatibility</h2>
        <p>
            Browsers versions, devices,
        </p>
    </section>
    <section>
        <h2>Additionnal <span class="highlighted-title">Capabilities</span></h2>
        <p>
            Push notifications, bluetooth, vibrations, ... (not enough time)
        </p>
    </section>
</div>
</template>

<script>
import { onMounted, onUnmounted } from 'vue';
let fadeInElements = [];

const isElemVisible = (el) => {
  let rect = el.getBoundingClientRect()
  let elemTop = rect.top + 200 // 200 = buffer
  let elemBottom = rect.bottom
  return elemTop < window.innerHeight && elemBottom >= 0
}

const handleScroll = (evt) => {
  for (let i = 0; i < fadeInElements.length; i++) {
    let elem = fadeInElements[i]
    if (isElemVisible(elem)) {
      elem.style.opacity = '1'
      elem.style.transform = 'scale(1)'
      fadeInElements.splice(i, 1) // only allow it to run once
    }
  }
}

export default {
  setup () {
    onMounted(() => {
      fadeInElements = Array.from(document.getElementsByClassName('pop-in'))
      document.addEventListener('scroll', handleScroll)
      handleScroll()
    })

    onUnmounted(() => {
      document.removeEventListener('scroll', handleScroll)
    })
  }
}
</script>