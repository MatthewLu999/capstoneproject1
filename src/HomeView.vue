<template>
<div>
    <HeaderOfMyPage />
  </div>
<br>
  <!-- Main Content -->
    <main>
        <!-- Carousel Section -->
        <section>
        <div class="carousel slide" data-ride="carousel">
            <ol class="carousel-indicators">
              <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
              <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
              <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
            </ol>
          <div class="carousel-inner">
            <div class="carousel-item active">
              <img class="d-block w-100" src="@img/slideshow3.jpeg" alt="First slide">
                <div class="carousel-caption d-none d-md-block">
                    <h3>BUILD PERFECT BODY WITH CLEAN MIND</h3>
                    <p>Founder of Zeus fitness Point</p>
                  </div>
            </div>
            <div class="carousel-item">
              <img class="d-block w-100" src="@img/slideshow2.jpg" alt="Second slide">
              <div class="carousel-caption d-none d-md-block">
                    <h3>BUILD PERFECT BODY WITH CLEAN MIND</h3>
                    <p>Founder of Zeus fitness Point</p>
                  </div>
            </div>
            <div class="carousel-item">
              <img class="d-block w-100" src="@img/slideshow1.jpg" alt="Third slide">
              <div class="carousel-caption d-none d-md-block">
                    <h3>BUILD PERFECT BODY WITH CLEAN MIND</h3>
                    <p>Founder of Zeus fitness Point</p>
                  </div>
            </div>
          </div>
</div>
       </section>
        <!-- Lose Weight Section -->
        <section id="lose-weight" class="workout-section">
            <h2>Lose Weight</h2>
            <p>How To Lose Weight Fast With Exercise</p>
            <div class="exercise-list">
                 <!-- dynamite content -->
              <div v-for="item in excerciselists" :key="item.id">
               <div class="card" style="width: 17em;">
                <img class="card-img-top" :src="item.img" alt="Card image cap" style="height: 15em;">
                <div class="card-body">
                  <h5 class="card-title"> {{ item.id  }}</h5>
                  <p class="card-text">{{ item.description  }}</p>
                </div>
              </div>
              </div>
            </div>
            <div class="pagination">
                <button>Previous</button>
                <button>1</button>
                <button>2</button>
                <button>Next</button>
            </div>
        </section>

        <!-- Release Stress Section -->
        <section id="release-stress" class="workout-section">
            <h2>Release Stress</h2>
            <p>Techniques to Reduce Stress and Anxiety</p>
            <div class="exercise-list">
               <!-- dynamite content -->
              <div v-for="item in medication" :key="item.id">
               <div class="card" style="width: 17em;">
                <img class="card-img-top" :src="item.img" alt="Card image cap" style="height: 15em;">
                <div class="card-body">
                  <h5 class="card-title">{{ item.id  }}</h5>
                  <p class="card-text">{{ item.description  }}</p>
                </div>
              </div>
              </div>
            </div>
            <div class="pagination">
                <button>Previous</button>
                <button>1</button>
                <button>2</button>
                <button>Next</button>
            </div>
        </section>

        <!-- Wellness News Section -->
        <section id="wellness-news">
            <h2>Wellness News</h2>
            <div class="news-content">
                <div class="image-container">
                    <img src="/images/news.jpg" alt="Health News">
                </div>
                <div class="text-container">
                    <p>A curated collection of health and wellness content from our team of medical professionals, including expert advice, news articles, health living resources, webinars, and blog posts. Providing you with insights, guidance, and inspiration to empower you on your personal wellness journey.</p>
                </div>
            </div>
        </section>
    </main>
<div>
    <FooterOfMyPage />
  </div>
</template>

<script>
import HeaderOfMyPage from './components/HeaderOfMyPage.vue'
import FooterOfMyPage from './components/FooterOfMyPage.vue'
export default {
  name: 'HomeView',
  data () {
    return {
      excerciselists: [{ id: 'Gym Motivation', description: 'Intense Workout', img: 'images/1.JPG' },
        { id: 'Treadmill Cardio', description: 'Steady Running', img: 'images/2.JPG' },
        { id: 'Outdoor Walking', description: 'Daily Steps', img: 'images/3.JPG' },
        { id: 'Yoga Pose Beginner', description: 'Balance Training', img: 'images/4.JPG' },
        { id: 'Core Workout', description: 'Sit-Up Effort', img: 'images/5.JPG' },
        { id: 'Sit-Up Beginner', description: 'Core Strengthening', img: 'images/6.JPG' },
        { id: 'Mountain Climbers', description: 'Intensity Boost', img: 'images/7.JPG' },
        { id: 'Stability Workout', description: 'Balance Coordination', img: 'images/8.JPG' }],
      medication: [{ id: 'Child Pose', description: 'Soothing Stretch', img: 'images/stress/8.JPG' },
        { id: 'Side Stretch', description: 'Flexibility Enhancer', img: 'images/stress/1.JPG' },
        { id: 'Seated Forward Bend', description: 'Peaceful Meditation', img: 'images/stress/2.JPG' },
        { id: 'Zen Pose Relax', description: 'Peaceful Meditation', img: 'images/stress/3.JPG' },
        { id: 'Bridge Pose In Minutes', description: 'Calmness Inducer', img: 'images/stress/4.JPG' },
        { id: 'Relaxation Pose', description: 'Muscle Relaxation', img: 'images/stress/5.JPG' },
        { id: 'Leg Stretch', description: '3 sets 8 reps', img: 'images/stress/6.JPG' },
        { id: 'Meditative Seating', description: 'Focus Enhancement', img: 'images/stress/7.JPG' }]
    }
  },
  components: {
    HeaderOfMyPage,
    FooterOfMyPage
  },
  methods: {
    createTable () {
      if (this.excerciselists.length > 0) {
        console.log('create data for lose weight')
        for (var i = 0; i < this.excerciselists.length; i++) {
          var description = this.excerciselists[i].description
          var picturePath = this.excerciselists[i].img
          var number = 'Workout ' + this.excerciselists[i].id
          // create dynamic table
          var cardObject = this.createCardElement(picturePath, number, description)
          console.log(cardObject)
        }
      } else {
        console.log('Cannot find the data')
      }
    },
    createCardElement (imageSrc, cardTitle, cardText) {
      // Create the outer div
      const card = document.createElement('div')
      card.className = 'card'
      card.style.width = '10rem'
      // Create the img element
      const img = document.createElement('img')
      img.className = 'card-img-top'
      img.src = imageSrc
      img.alt = 'Card image cap'
      // Create the card body
      const cardBody = document.createElement('div')
      cardBody.className = 'card-body'
      // Create the card title
      const title = document.createElement('h5')
      title.className = 'card-title'
      title.textContent = cardTitle
      // Create the card text
      const text = document.createElement('p')
      text.className = 'card-text'
      text.textContent = cardText
      // Append the title and text to the card body
      cardBody.appendChild(title)
      cardBody.appendChild(text)
      // Append the img and card body to the card
      card.appendChild(img)
      card.appendChild(cardBody)
      return card
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
    },
    getCookie (cname) {
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
    }
  }
}
</script>
