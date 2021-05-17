# Music-Player-Demo-By-Javascript
You must be add a song for play this app 



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="	https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.10.0/css/all.min.css">
    <link rel="stylesheet" href="style.css">
    
    <title>Music App</title>
    <style>
       
@import url('https://fonts.googleapis.com/css2?family=Jost:wght@300&display=swap');
*,
*::before,
*::after{
    margin: 0;
    padding:0%;
    box-sizing: border-box;
}

body{
    margin: 0;
    padding: 0;    

}

html{
    font-size:62.5%;
    font-family: 'Jost', sans-serif;
  

}

.main_div{
    width: 100vw;
    height: 100vh;
    background-color:#f6f6f6;
    display: grid;
    place-items: center;
 
}
.main_container #title{
    align-items: center;
    text-align: center;
    border-radius: 8rem;
    color: white;
    background-color:whitesmoke;
    padding:0%;
    margin: 0%;    
}

.main_container{
    width: 35rem;
    height:55rem;
    background-color:whitesmoke;
    border-radius: 6rem;
    text-align: center;
    padding:30px;
    box-shadow: 0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.938);

    font-weight: 500;
    background-color: black;

}


.main_container #title{
    text-transform:capitalize;
    text-align: center;
    letter-spacing: 0.2rem;
    word-spacing: 0.5rem;
    font-weight:bold;
    color: #171717;
    margin:2rem 0 0.5rem 0;
    font-size: 2.5rem;
    font-weight:500;
    text-shadow: 0 0.3rem 0.5rem rgba(0,0,0,0.3);

}


.main_container #artist{
    color: #cccaca;
    font-size: 2rem;
    text-transform: uppercase;
    font-weight: 300;
    margin-bottom: 4rem;
    letter-spacing: 0.1rem;
}

.img_container {
    width:25rem;
    height:25rem;
    margin:auto;


}
img{
    width:100%;
    height:100%;
    box-shadow: 0 1.2rem 3rem 0.5rem
     rgba(0, 0, 0, 0.54);
     border-radius: 50%;
     Object-fit: cover;
}

.music_controls{

}

.music_controls .fas{
    color:purple;
    font-size: 2rem;
    cursor: pointer;
    filter: drop-shadow(0 1.2rem 3rem 0.5rem rgba(0,0,0,0.4));

}


.music_controls{
    width:200px;
    display:flex;
    margin: auto;
    justify-content: space-between;
    margin-top:50px;
     align-items: center;

}


.music_controls .main_button {
    width: 5rem;
    height: 5rem;
    color: #f6f6f6;
    background-color: purple;
    border-radius: 50%;
    padding: 10px;
    font-size: 1.4rem;
    justify-content: center;
    display: flex;
    align-items: center;
}

.music_controls .fas:hover{
    color: grey;
}


i#play:hover {
    color: crimson;
    background-color: darkblue;
}


/* anime class add system */

.anime{

    animation:rotatePlayer 7s linear infinite;

}

@keyframes rotatePlayer{
    from{
        transform:rotate(0deg);
    }
    to{
        transform:rotate(360deg);
    }
}
    </style>
</head>
<body>
    
    <div class="main_div">
        <div class="main_container">
            <h2 id="title">Roxy Player</h2>
            <h3 id="artist">Music Player</h3>
            <div class="img_container">
                <img src="image/image.jpg" alt="samiul" class="anime" >
          </div>

       

            <audio src="Music/Hridoy_Khan_Obujh_Bhalobasha.mp3"></audio>
       

            <!-- controls -->
        <div class="music_controls">

        <i class="fas fa-backward " id="prev" title="Previous"></i>


        <i class="fas fa-play main_button" id="play" title="Play"></i>

        

        <i class="fas fa-forward" id="next" title="Next"></i>
   
        </div>
        </div>
    </div>

<!-- Now we will working about vanila js -->

<script>
    const play = document.getElementById('play');
    const img = document.querySelector("img");

    const music = document.querySelector('audio');
     //new data store
    const artist = document.getElementById('artist');
    const title = document.getElementById('title');
    const prev = document.getElementById('prev');
    const next = document.getElementById('next');

    
    const songs =[
    {
        name: "image",
        title: "English Song",
        artist:  "Justin Bibar"
    },

    {
        name: "logo",
        title: "Arabic song",
        artist:  "Arabian singer",
    },
  ,
    {
        name: "SamiulHasan-2",
        title: "Bangla song",
        artist:  "Hridoy khan Album"
    },
    {
        name: "samiul",
        title: "Hindi song",
        artist:  "The bigger"
    },
];



    let isPlaying = false;

    // for playing music

    const playMusic = () =>{
        isPlaying = true;
        music.play();

        play.classList.replace("fa-play", "fa-pause");

        play.classList.add("anime");
    };


//    for stop music

const pauseMusic =()=>{
        isPlaying = false;
        music.pause();

        play.classList.replace("fa-pause", "fa-play");

        play.classList.remove("anime");
    };
  
play.addEventListener("click", () =>{

// if(isPlaying){
//     pauseMusic();
// }else{
//     playMusic();
// }
isPlaying ? pauseMusic() : playMusic();
});

//changing the music data

const loadsong =(songs)=>{
title.textContent = songs.title;
artist.textContent = songs.artist;
music.src = "Music/" + songs.name + ".mp3";
img.src = "image/" + songs.name + ".jpg";

};

//loadsongs(songs[]);

songIndex = 0 ;

const nextSong =()=>{

    songIndex = (songIndex + 1 ) % songs.length;
    loadsong(songs[songIndex]);
    playMusic();
}

const prevSong =()=>{
  
    songIndex = (songIndex - 1 + songs.length) % songs.length;
    loadsong(songs[songIndex]);
    playMusic();
}

next.addEventListener("click", nextSong);
prev.addEventListener("click", prevSong);




</script>


</body>
</html>
