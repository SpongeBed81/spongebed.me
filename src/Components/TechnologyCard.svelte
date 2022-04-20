<script>
    export let name;
    export let type;
    export let color;
    export let img;
    export let height;
    export let width;
</script>

<style>


    
@media screen and (max-width: 850px) {
    #someTech {
        flex-direction: column;
    }

    #image {
        width: 100% !important;
        border-bottom-left-radius: 0px !important;
        border-bottom-style: solid;
        border-top-right-radius: 8px !important;
        border-bottom-width: 1px;
        border-bottom-color: rgba(49, 50, 50, 0.77); 
        border-right-style: none !important;
     
    }

    #image > img {
        margin-top: 10px !important;
        margin-bottom: 10px !important;
    }

    #nameContainer {
        width: 100% !important;
        border-bottom-left-radius: 0px !important;
        border-top-left-radius: 0px !important;
        border-bottom-style: solid;
        border-bottom-width: 1px;
        border-bottom-color: rgba(49, 50, 50, 0.77); 
        border-right-style: none !important;
    }
  }

    #someTech {
        margin-top: 10px;
        position: relative;
        border-style: solid;
        border-width: 1px;
        border-color: rgba(49, 50, 50, 0.77);
        width: 100%;
        border-radius: 8px;
        display: flex;
    }

 


    
   #image {
       position: relative;
       left: 0;
       width: 10%;
       border-bottom-left-radius: 8px;
       border-top-left-radius: 8px;
       display:flex;
        align-items:center;
        justify-content: space-evenly;      
   }

   #image > img {
    -webkit-user-drag: none;
    user-select: none;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;       
   }

    #nameContainer {
        flex-direction: column;
        border-right-style: solid;
        border-right-width: 1px;
        border-right-color: rgba(49, 50, 50, 0.77);
        width: 150px;
        line-height: 5px;
    }

    #type {
        flex-direction: column;
        width: 250px;
        line-height: 5px;
    }

 

    #nameContainer p:nth-child(1) {
        padding-left: 10px;
        font-family: 'IBM Plex Mono', monospace;
        color: rgb(205, 207, 208);
    }

    #nameContainer p:nth-child(2) {
        padding-left: 10px;
        font-family: 'Inter', sans-serif;
       color: rgb(136, 138, 139);
    }

    #type p:nth-child(1) {
        padding-left: 10px;
        font-family: 'IBM Plex Mono', monospace;
        color: rgb(205, 207, 208);
    }

    #type p:nth-child(2) {
        padding-left: 10px;
        font-family: 'Inter', sans-serif;
       color: rgb(136, 138, 139);
    }

    #techName {
        padding-top: 10px;
    }
</style>

<div id="someTech">
    <div id="image" style="background-color: {color}">
        <img src={img} alt="" style="width: {width + "px"}; height: {height + "px"}; position: relative">
    </div>
    <div id="nameContainer">
        <p id="techName">name</p>
        <p>{name}</p>
    </div>

    <div id="type">
        <p id="techName">type</p>
        <p>{type}</p>
    </div>
</div>