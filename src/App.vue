<script setup>
import { ref } from 'vue'
import SideNav from './components/SideNav.vue'
import Loading from './components/Loading.vue'

const userName = ref("Amir!!")
const onlineStatus = ref(true)
const githublink = ref("https://github.com/apmaxx")
const currentView = ref('portfolio')
const isNavigating = ref(false)

const thankYou = () => {
  alert('Thank you for your message!')
}

const handleNavigate = (view) => {
  isNavigating.value = true
  setTimeout(() => {
    currentView.value = view
    isNavigating.value = false
  }, 800)
}
</script>

<template>
  <div class="app-container">
    <Loading />
    <SideNav @navigate="handleNavigate" />

    <div v-if="currentView === 'portfolio' && !isNavigating">
      <main class="main-content">
      
      <section id="home" class="section home-section">
        <div class="hero-content">
          <div class="myname">
            <h1>Amir Pettigrew</h1>
          </div>
          <div class="myskills">
            <p>Full-Stack Developer • Designer • Animator • (Self-Proclaimed) Legend</p>
          </div>
          
          <button class="cont" @click="scrollToSection('about')"> Continue? </button>           

        </div>
      </section>

      
      <section id="about" class="section about-section">
        <div class="aboutme">
          <h2 class="me"> About Me </h2>
          <div class="bio">
            <p>Hello! My name is Amir and I am a rising full-stack developer looking to improve my skills and abilities! In the future, I would love to create my own social media application. I hope you enjoy my page and look forward to future news and updates! Here are some skills I am proficient in!</p>
             <div class="img1"> 
            <img src="./assets/html.png" width="150px" />
             </div>
             <div class="img2">
              <img src="./assets/css.png" width="150px" />
              </div>
              <div class="img3">
              <img src="./assets/javascript.png" width="150px" />
              </div>
              <div class="img4">
              <img src="./assets/javalogo.png" width="150px" />
              </div>
              <div class="img7">
              <img src="./assets/vue.png" width="150px" />
              </div>
              <div class="img8">
              <img src="./assets/Sql.png" width="150px" />
              </div>
              <div class="img9">
              <img src="./assets/flask.png" width="150px" />
              </div>
              <div class="img10">
              <img src="./assets/github.png" width="150px" />
              </div>
              <div class="img11">
              <img src="./assets/nginx.png" width="150px" />
              </div>
              <div class="img12">
              <img src="./assets/vs.png" width="150px" />
              </div>
              <div class="img13">
              <img src="./assets/adobe.webp" width="150px" />
              </div>
              <div class="img14">
              <img src="./assets/got.png" width="150px" />
              </div>
              </div>
        </div>
       
      </section>

     
      <section id="projects" class="section projects-section">
        <div class="projects">
          <h2 class="mypr"> Projects </h2> 
          <div class="skills-grid">
            <div class="skill-card">
              <p> Study Group Finder</p>
              <img src="./assets/scsu.png" width="500px"/>
              
            </div>
            <div class="skill-card">
              <p> Small Animation Trailer</p>
              <video controls width="500px">
                <source src="/src/assets/trailer.mp4" type="video/mp4" />
              </video>
             
            </div>
           
          </div>
        </div>
          <div class="kiriko">
            <p style="font-family: 'CustomFont'; font-size: 45px;"> Thank you for viewing! Hope you have a wonderful day!</p>
      <img src="/src/assets/kirko.gif" width="1000px" height="100px" />
      
      </div>
      </section>

    
    </main>
    </div>

    <div v-else-if="isNavigating" class="loading-overlay">
      <div class="loading-content">
        <div class="spinner"></div>
        <h3>Loading...</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  min-width: none;
  background-image: url('/src/assets/cyrene.gif');
  background-repeat: no-repeat;
  background-size: 117.5%;
  
}

.main-content {
  padding-left: 0; /* No fixed margin since sidebar is collapsible */
  min-height: 100vh;
}

.section {
  padding: 100px 40px;
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.home-section {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1) 0%, rgba(255, 255, 255, 0.05) 100%);
  
 
}

.hero-content {
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

.myname h1 {
  font-size: 80px;
  font-weight: bold;
  margin-bottom: 20px;
  color: rgb(255, 255, 255);
  text-shadow: 2px 9px 9px rgba(0, 0, 0, 0.3);
}

.myskills p {
  font-size: 1.5rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 40px;
   text-shadow: 2px 9px 9px rgba(0, 0, 0, 0.3);
}


 

.me{
  margin-left: 200px;
  color: #1e61cc;
  font-size: 50px;
  font-family: 'CustomFont'; 
}
.mypr{
  margin-top: -1790px;
  margin-left: 1600px;
  color: #1e61cc;
  font-size: 50px;
  font-family: 'CustomFont';
}


.aboutme{
  margin-left: 300px;
  
}

.bio {
  max-width: 600px;
  margin-right: 400px;
  
}

.bio p {
  font-size: 1.4rem;
  line-height: 1.8;
  color: #0d6aff;
  text-align: center;
  font-family: 'CustomFont';
}

@font-face {
  font-family: 'CustomFont';
  src: url('./assets/ComicNeue-Regular.ttf') format('truetype');
  font-style: normal;
}

.cont{
  border-radius: 20px ;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1) 0%, rgba(255, 255, 255, 0.05) 100%);
  font-family: 'CustomFont';
  font-size: 45px;
  font-style: italic;  
  color: rgb(255, 255, 255);
  text-shadow: 2px 9px 9px rgba(0, 0, 0, 0.3);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
  cursor: pointer;
}

.cont:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 25px rgb(73, 152, 255);
  
}

.about-card{
   background: white;
  padding: 40px 50px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(232, 255, 99, 0.1);
  text-align: center;
  transition: transform 0.3s ease;
  width: 100%;
  max-width: 600px;
}

.img1{
  margin-top: 50px;
  margin-bottom: 20px;
}

.img2{
  margin-top: 50px;
  margin-bottom: 20px;
}

.img3{
  margin-top: 50px;
  margin-bottom: 20px;
}

.img4{
  margin-top: -560px;
  margin-left: 250px;
}

.img5{
  margin-top: -560px;
  margin-left: 60px;
}

.img7{
  margin-top: 50px;
  margin-left: 250px;
}

.img8{
  margin-top: 100px;
  margin-left: 250px;
}

.img9{
  margin-top: -500px;
  margin-left: 500px;
}

.img10{
  margin-top: 70px;
  margin-left: 500px;
}

.img11{
  margin-top: 100px;
  margin-left: 500px;
}

.img12{
  margin-top: 100px; 
}

.img13{
  margin-top:-160px;
  margin-left: 250px;
}

.img14{
  margin-top: -150px;
  margin-left: 450px;
}


.skills-grid {
  margin-top: 50px;
  margin-left: 1400px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
  gap: 40px;
  
}

.skill-card {
  background: white;
  padding: 40px 50px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(232, 255, 99, 0.1);
  text-align: center;
  transition: transform 0.3s ease;
  width: 100%;
  max-width: 600px;
}

.skill-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgb(137, 201, 253);
}

.skill-card h3 {
  color: #1e3a8a;
  margin-bottom: 15px;
  font-size: 1.5rem;
  
}

.skill-card p {
  color: #1161ff;
  line-height: 1.0;
  font-family: 'CustomFont';
  
}

.contact-content {
  max-width: 6000px;
  margin: 0 auto;
  margin-top: 1500px;
}

.mycont{
  color: #1e61cc;
  font-size: 50px;
  margin-top: -1500px;
  margin-left: 1000px;
  font-family: 'CustomFont';
  text-align: center;
}

.kiriko{
  margin-top: 200px;
  margin-left: -1300px;
  min-width: 500px;
}
/* Responsive design */
@media (max-width: 768px) {
  .section {
    padding: 80px 20px;
  }

  .myname h1 {
    font-size: 2.5rem;
  }

  .myskills p {
    font-size: 1.2rem;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
  }

  .cta-button {
    width: 200px;
  }

  .skills-grid {
    grid-template-columns: 1fr;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .about-section h2,
  .skills-section h2,
  .projects-section h2,
  .contact-section h2 {
    font-size: 2rem;
  }

  .contact-form {
    padding: 30px 20px;
  }
}

@media (max-width: 480px) {
  .section {
    padding: 60px 15px;
  }

  .myname h1 {
    font-size: 2rem;
  }

  .skill-card,
  .project-card {
    padding: 25px 20px;
  }
}

.loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.loading-overlay .loading-content {
  text-align: center;
  color: white;
}

.loading-overlay .spinner {
  width: 50px;
  height: 50px;
  border: 4px solid rgba(255, 255, 255, 0.3);
  border-top: 4px solid white;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto 20px;
}

.loading-overlay h3 {
  font-size: 1.5rem;
  margin: 0;
}
</style>

<script>
export default {
  methods: {
    scrollToSection(sectionId) {
      const element = document.querySelector(`#${sectionId}`);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
}
</script>