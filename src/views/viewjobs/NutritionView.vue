<template>
<HeaderOfMyPage></HeaderOfMyPage>
 <section>
<!-- Carousel Section -->
        <section class="carousel">
            <div id="carouselExampleSlidesOnly" class="carousel slide" data-ride="carousel">
                <div class="carousel-inner">
                    <div class="carousel-item active">
                        <img class="d-block w-100" src="/images/fitness1.jpeg" alt="Healthy Food">
                    </div>
                    <div class="carousel-item">
                        <img class="d-block w-100" src="/images/slideshow2.jpg" alt="Nutrition">
                    </div>
                    <div class="carousel-item">
                        <img class="d-block w-100" src="/images/slideshow1.jpg" alt="Fitness">
                    </div>
                </div>
                <!-- Carousel Controls -->
                <a class="carousel-control-prev" href="#carouselExampleSlidesOnly" role="button" data-slide="prev">
                    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                    <span class="sr-only">Previous</span>
                </a>
                <a class="carousel-control-next" href="#carouselExampleSlidesOnly" role="button" data-slide="next">
                    <span class="carousel-control-next-icon" aria-hidden="true"></span>
                    <span class="sr-only">Next</span>
                </a>
            </div>
        </section>

        <!-- Meals Section -->
        <section id="meals" class="food1">
            <h2>Total - 2000 Calories for a Day</h2>
            <div class="food-list">
                <div class="food-item" @click="showMenu('breakfast')">
                    <img src="/images/breakfastL.jpg" alt="Breakfast">
                    <p>Breakfast</p>
                </div>
                <div class="food-item" @click="showMenu('lunch')">
                    <img src="/images/lunchL.jpg" alt="Lunch">
                    <p>Lunch</p>
                </div>
                <div class="food-item" @click="showMenu('dinner')">
                    <img src="/images/dinnerL.jpg" alt="Dinner">
                    <p>Dinner</p>
                </div>
            </div>
        </section>

        <!-- Breakfast Section -->
        <section id="breakfast" @click="updateHealthNews" class="meal-section hidden workout-section">
            <h2>Breakfast - Approximately 500-600 Calories</h2>
            <div class="meal-list">
                <a href="https://www.timhortons.ca/?lang=en&gad_source=1&gclid=CjwKCAjwgfm3BhBeEiwAFfxrG8_S8u2rhoEK1naN7CHsxbaq6taBjAYh2DLnYJArcCskKrK8iOD5lRoCW1sQAvD_BwE"></a>
                <!-- Breakfast items dynamically added by JS as cards -->
            </div>
        </section>

        <!-- Lunch Section -->
        <section id="lunch" @click="updateHealthNews" class="meal-section hidden workout-section">
            <h2>Lunch - Approximately 700-800 Calories</h2>
            <div class="meal-list">
                <!-- Lunch items dynamically added by JS as cards -->
            </div>
        </section>

        <!-- Dinner Section -->
        <section id="dinner" @click="updateHealthNews" class="meal-section hidden workout-section">
            <h2>Dinner - Approximately 600-700 Calories</h2>
            <div class="meal-list">
                <!-- Dinner items dynamically added by JS as cards -->
            </div>
        </section>
</section>
<FooterOfMyPage></FooterOfMyPage>
</template>

<script>
import HeaderOfMyPage from '../../components/HeaderOfMyPage.vue'
import FooterOfMyPage from '../../components/FooterOfMyPage.vue'
export default {
  name: 'NutritionView',
  components: {
    HeaderOfMyPage,
    FooterOfMyPage
  },
  data () {
    return {
      images: ['/images/fitness1.jpeg', '/images/slideshow2.jpg', '/images/slideshow1.jpg'],
      currentIndex: 0,
      totalnewswatched: 0
    }
  },
  mounted () {
    // =========
    // DOM loaded event
    // Show breakfast by default
    this.showMenu('breakfast')
    // Add breakfast items
    const breakfastItems = [
      { name: 'Tim Hortons - Bagel & Cream Cheese', calories: 510, image: '/images/tim1.jpg' },
      { name: 'Tim Hortons - Breakfast Sandwich', calories: 535, image: '/images/timbreakfastsandwich.jpg' },
      { name: 'Tim Hortons - Hash Browns', calories: 560, image: '/images/hashbrowntim.jpg' }
    ]
    this.addMenuItems('breakfast', breakfastItems, 'breakfast')
    // Add lunch items
    const lunchItems = [
      { name: 'A&W - Teen Burger', calories: 790, image: '/images/teenburger.jpg' },
      { name: 'A&W - Sweet Potato Fries', calories: 710, image: '/images/sweetpatatofries.jpg' },
      { name: 'A&W - Salad', calories: 765, image: '/images/salad.jpg' }
    ]
    this.addMenuItems('lunch', lunchItems, 'lunch')
    // Add dinner items
    const dinnerItems = [
      { name: 'Harvey - Grilled Chicken Sandwich', calories: 670, image: '/images/sandwichL.jpg' },
      { name: 'Harvey - Onion Rings', calories: 620, image: '/images/harvey2.jpg' },
      { name: 'Harvey - Chocolate Milkshake', calories: 600, image: '/images/proteinshake1.jpg' }
    ]
    this.addMenuItems('dinner', dinnerItems, 'dinner')
    // Start the automatic slideshow after the DOM is loaded
    this.startSlideshow()
  },
  methods: {
    updateHealthNews () {
      this.totalnewswatched++
      console.log(this.totalnewswatched)
      var currentNumbernews = this.getCookieforArray('todaynewswatched')
      var newNumbervideo = currentNumbernews + this.totalnewswatched
      this.deleteCookie('todaynewswatched')
      this.setCookieforArray('todaynewswatched', newNumbervideo, 365)
    },
    showSlide (index) {
      const carouselItems = document.querySelectorAll('.carousel-item')
      carouselItems.forEach((item, i) => {
        item.classList.remove('active')
        if (i === index) {
          item.classList.add('active')
        }
      })
    },
    nextSlide () {
      this.currentIndex = (this.currentIndex + 1) % this.images.length
      this.showSlide(this.currentIndex)
    },
    prevSlide () {
      this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length
      this.showSlide(this.currentIndex)
    },
    startSlideshow () {
      setInterval(() => {
        this.nextSlide()
        // Change the image automatically every 5 seconds
      }, 5000)
    },
    showMenu (menu) {
      document.querySelectorAll('.meal-section').forEach(section => {
        section.classList.add('hidden')
      })
      document.getElementById(menu).classList.remove('hidden')
    },
    addMenuItems (sectionId, items, menuType) {
      const section = document.querySelector(`#${sectionId} .meal-list`)
      section.innerHTML = ''
      // Set the redirect URL based on the menu type
      let redirectUrl = ''
      if (menuType === 'breakfast') {
        redirectUrl = 'https://www.timhortons.ca/?lang=en&gad_source=1&gclid=CjwKCAjwgfm3BhBeEiwAFfxrG8_S8u2rhoEK1naN7CHsxbaq6taBjAYh2DLnYJArcCskKrK8iOD5lRoCW1sQAvD_BwE'
      } else if (menuType === 'lunch') {
        redirectUrl = 'https://web.aw.ca/en/home'
      } else if (menuType === 'dinner') {
        redirectUrl = 'https://www.harveys.ca/en/locations/mb/winnipeg'
      }
      // Add the menu items to the section
      items.forEach(item => {
        const card = document.createElement('div')
        card.classList.add('card')
        card.innerHTML = `
            <a href='${redirectUrl}' target='_blank'>
                <img src='${item.image}' alt='${item.name}'>
                <div class='card-body'>
                    <h5 class='card-title'>${item.name}</h5>
                  <p class='card-text'>${item.calories} Calories</p>
                </div>
            </a>
        `
        section.appendChild(card)
      })
    },
    setCookieforArray (name, value, days) {
      var expires = ''
      if (days) {
        var date = new Date()
        date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000))
        expires = '; expires=' + date.toUTCString()
      }
      document.cookie = name + '=' + (JSON.stringify(value) || '') + expires + '; path=/'
    },
    getCookieforArray (name) {
      var nameEQ = name + '='
      var ca = document.cookie.split(';')
      for (var i = 0; i < ca.length; i++) {
        var c = ca[i]
        while (c.charAt(0) === ' ') c = c.substring(1, c.length)
        if (c.indexOf(nameEQ) === 0) {
          return JSON.parse(c.substring(nameEQ.length, c.length))
        }
      }
      return null
    },
    deleteCookie (cookieName) {
      // Set the cookie's expiration date to a past date
      document.cookie = cookieName + '=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;'
    }
  }
}
</script>
<style>
</style>
