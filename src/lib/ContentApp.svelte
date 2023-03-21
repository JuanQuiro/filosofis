<script>
    import {queryGlobal} from '../store/stores'
    let defaultImg = "https://via.placeholder.com/600x300.png?text=Si,+No,+Tal+Vez."
    let answerApp = ""
    
    $: {
        
        if ( $queryGlobal[0] === "¿") {
        fetch("https://yesno.wtf/api")
        .then(res => res.json())
        .then(res => (defaultImg = res.image,answerApp = (res.answer == "yes") ? "Si" :(res.answer == "no") ? "No" : (res.answer == "maybe") ? "Tal Vez" : ""));
        }
    }
    
</script>

<div class=" bg-base-200 grid text-center justify-center p-5 mt-5">
    <h2 class=" text-3xl first-letter  text-accent-focus">{$queryGlobal}</h2>
    <img width="600" height="300" src={defaultImg} alt="Si, no, tal vez" srcset="">
    <p class="text-3xl capitalize text-accent">{answerApp}</p>
</div>