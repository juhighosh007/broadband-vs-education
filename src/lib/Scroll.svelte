<script>
    let { sticky, scrolly, backgroundImage } = $props(); 
</script>

<div class="wrapper" >
    <div class="bgImage" style="background-image: url({backgroundImage});"></div>
    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
    .wrapper {
        position: relative;
        background-color: transparent;
    }

    .bgImage {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
        opacity: 0.9;
        z-index: -1;
    }

    .scrolly {
        display: flex;
        flex-direction: column;
        flex: 1 1;
        z-index: 1; 
    }


    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            width: 100vw;
        }

        .scrolly {
            flex: 1 1 auto;
            min-width: 100%;
            position: static; 
            transform: none;
        }

        
    }
</style>
