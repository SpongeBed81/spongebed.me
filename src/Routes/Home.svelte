<script>

import { onMount } from "svelte"
import TechnologyCard from "../Components/TechnologyCard.svelte"
import CommunityCard from "../Components/CommunityCard.svelte"
import ProjectCard from "../Components/ProjectCard.svelte"
let isOpen = false
onMount(async() => {

    fetch("https://api.lanyard.rest/v1/users/407486004505870336")
    .then(response => response.json())
    .then(data => {
        document.querySelector("#status").innerHTML = data.data.discord_status.replace("dnd", "Do not disturb").replace("idle", "Idle").replace("online", "Online").replace("offline", "Offline")
        let status = data.data.discord_status
        let color = document.querySelector("#statusColor")
        if(status == "dnd") {
            color.style.backgroundColor = "#c2152f"
        } else if(status == "idle") {
            color.style.backgroundColor = "#c9a70e"
        } else if(status == "online") {
            color.style.backgroundColor = "#71b814"
        }
    });

    const tapsounds = ['tap1.ogg', 'tap2.ogg', 'tap3.ogg', 'tap4.ogg']
function playTapSound() {
    let random = Math.floor(Math.random() * tapsounds.length);
    if (tapsounds[random] == 'tap1.ogg') {
        document.getElementById('tap1-sound').play();
    } else if (tapsounds[random] == 'tap2.ogg') {
        document.getElementById('tap2-sound').play();
    } else if (tapsounds[random] == 'tap3.ogg') {
        document.getElementById('tap3-sound').play();
    } else if (tapsounds[random] == 'tap4.ogg') {
        document.getElementById('tap4-sound').play();
    }
}
document.addEventListener("click", playTapSound);

window.addEventListener("resize", function(event) {
    if(isOpen == true && document.body.clientWidth > 500) {
        navbarHandler()
    }
})

})


function smoothScroll(query){
    document.querySelector(query).scrollIntoView({
        behavior: 'smooth'
    });
}

function navbarHandler() {
    if(isOpen == true) {
        isOpen = false

        let parent = document.querySelector("#navbar")
       while (parent.firstChild) {
        parent.firstChild.remove()
    }
        parent.style.flexDirection = "row"
        document.querySelector("#navbar").style.alignItems = "center"
        document.querySelector("#navbar").style.height = "" 
        document.querySelector("#navbar").style.justifyContent = "space-evenly" 

        let parag = document.createElement("p")
        parag.innerHTML = "spongebed."
       parag.id = "name"
       parag.style.color = "rgb(220, 214, 214)"
       parag.style.fontFamily = "Inter, sans-serif"
       parag.style.fontWeight = "700"
       parag.style.fontSize = "large"

       let controller = document.createElement("p")
        controller.id = "controller"
        controller.style.color = "rgb(220, 214, 214)"
        controller.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" id="expand" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svelte-d564ve"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>`
       parent.appendChild(parag)
       parent.appendChild(controller)

       document.getElementById("controller").addEventListener("click", () => {
           navbarHandler()
       });


    } else {
        isOpen = true
        document.querySelector("#navbar").style.setProperty("align-items", "")
        document.querySelector("#navbar").style.height = "100%"
       let parent = document.querySelector("#navbar")
       while (parent.firstChild) {
        parent.firstChild.remove()
    }
       document.querySelector("#navbar").style.setProperty("flex-direction", "column")
       document.querySelector("#navbar").style.justifyContent = "flex-start"
       let cr = document.createElement("div")
       cr.id = "header"
       cr.style.width = "100%"
       cr.style.height = "70px"
       cr.style.display = "flex"
       cr.style.marginTop = "10%"

       let parag = document.createElement("p")
       parag.innerHTML = "spongebed."
       parag.id = "name"
       parag.style.color = "rgb(220, 214, 214)"
       parag.style.fontFamily = "Inter, sans-serif"
       parag.style.fontWeight = "700"
       parag.style.fontSize = "large"
       parag.style.marginLeft = "2rem"

       let icon = document.createElement("p")
       icon.id = "controller"
       icon.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>`
       icon.style.color = "rgb(220, 214, 214)"
       icon.style.marginLeft = "auto"
       icon.style.marginRight = "3rem"


       let routesDiv = document.createElement("div")
        routesDiv.style.height = "40%"
        routesDiv.style.width = "100%"
        routesDiv.style.display = "flex"
        routesDiv.style.flexDirection = "column"
        routesDiv.style.justifyContent = "space-evenly"

        let home = document.createElement("p")
        home.innerText = "home"
        home.id = "home"
        home.style.setProperty("color", "rgb(183, 178, 178)")
      
        home.style.setProperty("font-family", "Inter, sans-serif")
        home.style.setProperty("font-weight", "400")
        home.style.marginLeft = "2rem"

        let technologies = document.createElement("p")
        technologies.innerText = "technologies"
        technologies.id = "technologies"
        technologies.style.setProperty("color", "rgb(183, 178, 178)")
      
        technologies.style.setProperty("font-family", "Inter, sans-serif")
        technologies.style.setProperty("font-weight", "400")
        technologies.style.marginLeft = "2rem"

        let projects = document.createElement("p")
        projects.innerText = "projects"
        projects.id = "projects"
        projects.style.setProperty("color", "rgb(183, 178, 178)")

        projects.style.setProperty("font-family", "Inter, sans-serif")
        projects.style.setProperty("font-weight", "400")
        projects.style.marginLeft = "2rem"

        let contact = document.createElement("p")
        contact.innerText = "contact"
        contact.id = "contact"
        contact.style.setProperty("color", "rgb(183, 178, 178)")
 
        contact.style.setProperty("font-family", "Inter, sans-serif")
        contact.style.setProperty("font-weight", "400")
        contact.style.marginLeft = "2rem"
      
      
       
       cr.appendChild(parag)
       cr.appendChild(icon)
       parent.appendChild(cr)
       routesDiv.appendChild(home)
       routesDiv.appendChild(technologies)
       routesDiv.appendChild(projects)
       routesDiv.appendChild(contact)
       parent.appendChild(routesDiv)

       document.getElementById("controller").addEventListener("click", () => {
           navbarHandler()
       });

       
       document.getElementById("home").addEventListener("click", () => {
           smoothScroll("#main")
       });

       document.getElementById("technologies").addEventListener("click", () => {
           smoothScroll("#technologiesDiv")
       });

       document.getElementById("projects").addEventListener("click", () => {
           smoothScroll("#projectsDiv")
       });

       document.getElementById("contact").addEventListener("click", () => {
           smoothScroll("#contactDiv")
       });
       
 
    }
}


</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@300&display=swap');
    :global(body) {
        background-color: #000;
        overflow: none; /* Hide scrollbars */
    }


    @media screen and (max-width: 820px) {
    #pp {
        display: none;
    }
    #yazi {
        width: 90% !important;
    }
  }

 

  
  @media screen and (max-width: 970px) {
    #titleTech, #projectsTitle2, #projectsTitle, #titleContact {
        text-align: center;
        padding-left: 0rem !important;
    }

    #contactButtons {
        margin-left: 0 !important;
        margin: 0 auto !important;
    }

  }

  
  @media screen and (max-width: 500px) {
    #home, #technologies, #projects, #contact {
        display: none !important;
    }

    #expand {
        display: block !important;
    }

  }


    


  #mainHolder {
      position: absolute;
      left: 0%;
      top: 0%;
      display: flex;
      flex-direction: column;
      width: 100%;
      height: 100%;
  }

  

    #navbar {
        position: fixed;
        width: 100%;
        height: 70px;
        top: 0;
        background-color: rgba(12, 11, 11, 0.871);
        left: 0;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
        border-bottom-style: solid;
        border-bottom-color: #1c1a1a;
        border-bottom-width: 1px;
    }

    #main {
        position: relative;
        left: 0;
        width: 100%;
        height: 100%;
        display:flex;
        align-items:center;
        justify-content: space-evenly;
    }

    #yazi {
        position: relative;
        width: 50%;
        word-break: break-all;
    }


    #title {
        color: rgba(159, 156, 156, 0.9);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: x-large;

    }

    #description {
        color: rgba(135, 131, 131, 0.9);
        font-family: Inter, sans-serif;
        font-weight: 400;
   
    }

    #holder {
        position: relative;
        top: 0;
        left: 0;
        width: 100%;
        overflow: auto;
    }

    #pp {
        border-radius: 50%;
        --tw-border-opacity: 1;
        border-color: rgb(31 41 55/var(--tw-border-opacity));
        border-style: solid;
        border-width: 3px;
    -webkit-user-drag: none;
    user-select: none;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;        
    }

    #statusDiv {
        display: flex;
        height: 30px;
        align-items:center;
    }
  

    #statusColor {
        position: relative;
        width: 10px;
        height: 10px;
        background-color: #2a2b28;
        border-radius: 50%;
    }

    #status {
        position: relative;
        padding-left: 10px;
        color: rgb(92, 89, 89);
        
    }

    

    #name {
        color: rgb(220, 214, 214);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: large;
    }

    #navbar {
        display: flex;
        justify-content: space-evenly;
        z-index: 99;
    }

    #contact, #projects, #home, #technologies {
        color: rgb(183, 178, 178);       
    }
      
    #contact:hover {
        cursor: pointer;
        color: rgb(220, 214, 214);
    }
    #projects:hover {
        cursor: pointer;
        color: rgb(220, 214, 214);
    }
    #home:hover {
        cursor: pointer;
        color: rgb(220, 214, 214);
    }

    #technologies:hover {
        cursor: pointer;
        color: rgb(220, 214, 214);
    }

    #technologiesDiv {
        position: relative;
        left: 0%;
        width: 100%;
        overflow:auto; 
        background-color: #000;
    }

  

    #titleTech {
        position: relative;
        padding-left: 7rem;
        color: rgb(205, 201, 201);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: x-large;
    
    }

    
    #titleContact {
        position: relative;
        padding-left: 7rem;
        color: rgb(205, 201, 201);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: x-large;
 
    }

    #techs {
        position: relative;
        margin: 0 auto;
        width: 85%;
     
    }

    #projectsEl {
        position: relative;
        margin: 0 auto;
        width: 85%;
  
    }

    #projectsDiv {
        position: relative;
        left: 0%;
        width: 100%;
        overflow:auto; 
        background-color: #000;
    }

    #projectsTitle {
        position: relative;
        padding-left: 7rem;
        color: rgb(205, 201, 201);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: x-large;
  
    }

    #comms {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-evenly;
    }

    #projectsTitle2 {
        position: relative;
        padding-left: 7rem;
        color: rgb(205, 201, 201);
        font-family: Inter, sans-serif;
        font-weight: 700;
        font-size: x-large;

    }

 

    * {
        -webkit-user-select: none; /* Safari */        
        -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* IE10+/Edge */
        user-select: none; /* Standard */     
    }

    #expand {
       color: rgb(183, 178, 178);
        display: none;
    }

    #contactDiv {
        position: relative;
        left: 0%;
        width: 100%;
        overflow:auto; 
        background-color: #000;
    }

    #contactButtons {
        margin-left: 7rem;
        position: relative;
        width: 85%;
        display: flex;
        flex-wrap: wrap;
        margin-top: 50px;
        justify-content: space-between;
    }

    :root {
    --darkest: rgb(10, 10, 10);
    --dark: rgb(20, 20, 20);
    --normal: rgb(30,30,30);
    --cyan: rgb(113, 226, 226);
    --light: rgb(40,40,40);
    --lighter: rgb(50,50,50);
    --lightest: rgb(70,70,70);
    --white: rgb(150,150,150);
    --whitest: rgb(200,200,200);
}

    #contactButtons > button {
        height: 50px;
        width: 100px;
        border: solid 1px var(--lightest);
        border-radius: 6px;
        cursor: pointer;
        transition: all 250ms;
        background-color: transparent;
        color: rgb(231, 224, 224);
        font-family: Inter, sans-serif;
        font-weight: 400;
    }

   



    #contactButtons > button:hover {
        background-color: var(--lightest);
    }



</style>
<sounds>
    <audio id="tap1-sound" src="assets/sounds/tap1.ogg"></audio>
    <audio id="tap2-sound" src="assets/sounds/tap2.ogg"></audio>
    <audio id="tap3-sound" src="assets/sounds/tap3.ogg"></audio>
    <audio id="tap4-sound" src="assets/sounds/tap4.ogg"></audio>
</sounds>

  

<div id="mainHolder">
    <div id="navbar" style="align-items:center;">
        <p id="name">spongebed.</p>
            <p id="home" on:click={() => smoothScroll("#main")}>home</p>
            <p id="technologies" on:click={() => smoothScroll("#technologiesDiv")}>technologies</p>
            <p id="projects" on:click={() => smoothScroll("#projectsDiv")}>projects</p>
            <p id="contact" on:click={() => smoothScroll("#contactDiv")}>contact</p>
        <p on:click={navbarHandler}><svg xmlns="http://www.w3.org/2000/svg" id="expand" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg></p>
    </div>
    <div id="holder">
        <div id="main">
            <div id="yazi">
                <p id="title">😝 Your full-stack developer with a trash front-end</p>
                <p id="description">Hello! my name is SpongeBed. I'm a 14 year old full-stack developer living in Turkey. <br> I have been programming for 3 years and I mostly use JavaScript and C# in my projects.</p>
                <div id="statusDiv">
                    <div id="statusColor"></div>
                    <p id="status">Loading status...</p>
                </div>
            </div>
            <img src="assets/images/pp.png" alt="" id="pp">
        </div>
        <div id="technologiesDiv">
            <p id="titleTech">👨🏻‍💻 Technologies I use</p>
            <div id="techs">
                <TechnologyCard name="javascript" type="programming language" color="#e3cf1b" width="40" height="40" img="assets/images/javascript.png"></TechnologyCard>
                <TechnologyCard name="c sharp" type="programming language" color="#1d0341" width="35" height="38" img="assets/images/csharp.png"></TechnologyCard>
                <TechnologyCard name="nodeJS" type="runtime" color="#396b2a" width="35" height="38" img="assets/images/nodejs.png"></TechnologyCard>
                <TechnologyCard name=".NET" type="framework" color="#3606a9" width="35" height="38" img="assets/images/dotnet.png"></TechnologyCard>
                <TechnologyCard name="svelte" type="framework" color="#c24922" width="30" height="38" img="assets/images/svelte.png"></TechnologyCard>
            </div>
        
          
        </div>
        <div id="projectsDiv">
            <p id="projectsTitle">👥 Communities</p>
            <div id="comms">
                <CommunityCard name="CodAre Development" role="Trial Moderator" img="assets/images/codare.gif" desc="CodAre is a Discord bot development
and software community. It is the
most crowded Discord community
about software in Turkey."></CommunityCard>
        
        <CommunityCard name="Vezalan Software" role="Team Lead" img="assets/images/vezalan.webp" desc="Vezalan Software is a software 
company with currently 8 members. 
Most prefered languages among the
company is C#, JavaScript and PHP."></CommunityCard>
        
        <CommunityCard name="Nuxonic" role="Trial Moderator" img="assets/images/nuxonic.png" desc="Nuxonic is a community project 
where people who want to learn 
software or develop projects socially."></CommunityCard>
            </div>
            <p id="projectsTitle2">💻 Projects</p>
            <div id="projectsEl">
                <ProjectCard name="Merge" lang="typescript, csharp" desc="A privacy focused chatting application to communicate with your friends or communities."></ProjectCard>
                <ProjectCard name="Plex.js" lang="javascript" desc="A powerful Discord API wrapper to quickly build your Discord bots easy and lightweight."></ProjectCard>   
                <ProjectCard name="turkanimetv-dl" lang="javascript" desc="A fast npm package to download anime videos from turkanime.co."></ProjectCard>
                <ProjectCard name="turkanimetv-api" lang="javascript, csharp" desc="A fast unofficial API wrapper to fetch data from turkanime.co."></ProjectCard>
                <ProjectCard name="v12tov13" lang="javascript" desc="A program to convert your Discord.js v12 code to v13 automaticly."></ProjectCard>
                <ProjectCard name="djs-threads" lang="javascript" desc="Npm package to use thread feature in all Discord.js versions."></ProjectCard>
            </div>
        </div>
        <div id="contactDiv">
            <p id="titleContact">📭 Contact me</p>
            <div id="contactButtons">
                <button on:click={() => (window.open("https://lookup.guru/407486004505870336", "_blank").focus())}>Discord</button>
                <button on:click={() => (window.open("https://github.com/SpongeBed81", "_blank").focus())}>GitHub</button>
                <button  on:click={() => (window.open("https://instagram.com/spongebed81/", "_blank").focus())}>Instagram</button>
            </div>
        </div>
    </div>
</div>

