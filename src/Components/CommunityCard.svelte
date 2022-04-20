<script>

    export let img;
    export let name;
    export let role;
    export let desc;



</script>

<style>



    #someCom > p:nth-child(2) {
        font-family: Inter, sans-serif;
        color: rgb(216, 210, 210);
        font-weight: 700;
        padding-left: 10px;
    }



    #comImage {
        display: flex;
        align-items: center;
        height: 8rem;
        border-bottom-style: solid;
        border-bottom-width: 1px;
        border-bottom-color: rgba(49, 50, 50, 0.77);
    }

    #infos {
        display: flex;
        flex-direction: column;
        line-height: 0px;
    }

    #infos > p {
        -webkit-user-select: none; /* Safari */        
        -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* IE10+/Edge */
        user-select: none; /* Standard */  
    }

    #infos p:nth-child(1){
        font-family: Inter, sans-serif;
        color: rgb(215, 209, 209);
        font-weight: 700;
        padding-left: 10px;
    }

    #infos p:nth-child(2) {
        font-family: Inter, sans-serif;
        color: rgb(165, 160, 160);
        font-weight: 700;
        padding-left: 10px;
    }

    #comImage img {
        margin-left: 1rem;
        margin-top: 1rem;
        border-radius: 25%;
        -webkit-user-drag: none;
    user-select: none;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;      
    }

    #someCom {
        height: 20rem;
        width: 300px;
        border-style: solid;
        border-width: 1px;
        border-color: rgba(49, 50, 50, 0.77);
        border-radius: 8px;
        margin-top: 15px;
        word-break: break-all;
        white-space: pre-line;
    }

    #someCom p, pre {
        -webkit-user-select: none; /* Safari */        
        -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* IE10+/Edge */
        user-select: none; /* Standard */  
    }

    
    #descriptionCom {
        font-family: Inter, sans-serif;
        color: rgb(205, 201, 201);
        font-weight: 400;
        padding-left: 10px;
    }


</style>


   <div id="someCom">
    <div id="comImage">
        <img src={img} alt="" style="width: 80px; height: 80px;">
        <div id="infos">
            <p>{name}</p>
            <p>{role}</p>
        </div>
    </div>
    <p>What</p>
    <pre id="descriptionCom">{desc}</pre>
</div>