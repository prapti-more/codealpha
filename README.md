<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Image Gallery</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:#f4f4f4;
    padding:20px;
}

h1{
    text-align:center;
    margin-bottom:20px;
    color:#333;
}

.gallery{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:15px;
}

.gallery img{
    width:100%;
    height:220px;
    object-fit:cover;
    border-radius:10px;
    cursor:pointer;
    transition:0.4s ease;
}

.gallery img:hover{
    transform:scale(1.05);
    box-shadow:0 8px 20px rgba(0,0,0,0.2);
}

/* Responsive */
@media(max-width:600px){
    .gallery img{
        height:180px;
    }
}
</style>
</head>

<body>

<h1>Responsive Image Gallery</h1>

<div class="gallery">
    <img src="https://picsum.photos/id/1015/500/300" alt="Image 1">
    <img src="https://picsum.photos/id/1016/500/300" alt="Image 2">
    <img src="https://picsum.photos/id/1018/500/300" alt="Image 3">
    <img src="https://picsum.photos/id/1020/500/300" alt="Image 4">
    <img src="https://picsum.photos/id/1024/500/300" alt="Image 5">
    <img src="https://picsum.photos/id/1035/500/300" alt="Image 6">
</div>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced Image Gallery</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:#f2f2f2;
    padding:20px;
}

h1{
    text-align:center;
    margin-bottom:20px;
    color:#333;
}

.gallery{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:15px;
}

.gallery img{
    width:100%;
    height:220px;
    object-fit:cover;
    border-radius:10px;
    cursor:pointer;
    transition:0.4s ease;
}

.gallery img:hover{
    transform:scale(1.05);
    box-shadow:0 8px 20px rgba(0,0,0,0.3);
    filter:brightness(1.1);
}

/* Lightbox */
.lightbox{
    display:none;
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.9);
    justify-content:center;
    align-items:center;
    z-index:1000;
}

.lightbox img{
    max-width:80%;
    max-height:80%;
    border-radius:10px;
    animation:zoom 0.4s ease;
}

@keyframes zoom{
    from{transform:scale(0.7);}
    to{transform:scale(1);}
}

.close{
    position:absolute;
    top:20px;
    right:30px;
    color:white;
    font-size:35px;
    cursor:pointer;
}

.prev,.next{
    position:absolute;
    top:50%;
    transform:translateY(-50%);
    color:white;
    font-size:45px;
    cursor:pointer;
    padding:10px;
    user-select:none;
}

.prev{left:20px;}
.next{right:20px;}

.prev:hover,.next:hover,.close:hover{
    color:#ff9800;
}

@media(max-width:600px){
    .gallery img{
        height:180px;
    }

    .lightbox img{
        max-width:95%;
    }
}
</style>
</head>

<body>

<h1>Advanced Image Gallery</h1>

<div class="gallery">
    <img src="https://picsum.photos/id/1015/600/400" onclick="openLightbox(0)">
    <img src="https://picsum.photos/id/1016/600/400" onclick="openLightbox(1)">
    <img src="https://picsum.photos/id/1018/600/400" onclick="openLightbox(2)">
    <img src="https://picsum.photos/id/1020/600/400" onclick="openLightbox(3)">
    <img src="https://picsum.photos/id/1024/600/400" onclick="openLightbox(4)">
    <img src="https://picsum.photos/id/1035/600/400" onclick="openLightbox(5)">
</div>

<div class="lightbox" id="lightbox">
    <span class="close" onclick="closeLightbox()">&times;</span>
    <span class="prev" onclick="changeSlide(-1)">&#10094;</span>
    <img id="lightbox-img">
    <span class="next" onclick="changeSlide(1)">&#10095;</span>
</div>

<script>
const images = [
"https://picsum.photos/id/1015/600/400",
"https://picsum.photos/id/1016/600/400",
"https://picsum.photos/id/1018/600/400",
"https://picsum.photos/id/1020/600/400",
"https://picsum.photos/id/1024/600/400",
"https://picsum.photos/id/1035/600/400"
];

let currentIndex = 0;

function openLightbox(index){
    currentIndex = index;
    document.getElementById("lightbox").style.display = "flex";
    document.getElementById("lightbox-img").src = images[currentIndex];
}

function closeLightbox(){
    document.getElementById("lightbox").style.display = "none";
}

function changeSlide(step){
    currentIndex += step;

    if(currentIndex < 0){
        currentIndex = images.length - 1;
    }

    if(currentIndex >= images.length){
        currentIndex = 0;
    }

    document.getElementById("lightbox-img").src = images[currentIndex];
}
</script>

</body>
</html> 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Responsive Filter Image Gallery</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    background:#f4f4f4;
    padding:20px;
}

h1{
    text-align:center;
    margin-bottom:20px;
    color:#333;
}

/* Filter Buttons */
.filter-buttons{
    text-align:center;
    margin-bottom:20px;
}

.filter-buttons button{
    padding:10px 18px;
    margin:5px;
    border:none;
    background:#333;
    color:white;
    border-radius:6px;
    cursor:pointer;
    transition:0.3s;
}

.filter-buttons button:hover,
.filter-buttons button.active{
    background:#ff9800;
}

/* Gallery */
.gallery{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:15px;
}

.gallery-item{
    overflow:hidden;
    border-radius:10px;
    display:block;
}

.gallery-item img{
    width:100%;
    height:220px;
    object-fit:cover;
    cursor:pointer;
    transition:0.4s ease;
}

.gallery-item img:hover{
    transform:scale(1.08);
    filter:brightness(1.1);
}

/* Lightbox */
.lightbox{
    display:none;
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.9);
    justify-content:center;
    align-items:center;
    z-index:999;
}

.lightbox img{
    max-width:90%;
    max-height:80%;
    border-radius:10px;
}

.close,.prev,.next{
    position:absolute;
    color:white;
    font-size:35px;
    cursor:pointer;
    user-select:none;
}

.close{
    top:20px;
    right:30px;
}

.prev{
    left:20px;
    top:50%;
}

.next{
    right:20px;
    top:50%;
}

.close:hover,.prev:hover,.next:hover{
    color:#ff9800;
}

/* Mobile Responsive */
@media(max-width:768px){
    .gallery{
        grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
    }

    .gallery-item img{
        height:180px;
    }
}

@media(max-width:480px){
    h1{
        font-size:24px;
    }

    .filter-buttons button{
        padding:8px 12px;
        font-size:14px;
    }

    .gallery{
        grid-template-columns:1fr;
    }

    .gallery-item img{
        height:220px;
    }
}
</style>
</head>

<body>

<h1>Responsive Image Gallery</h1>

<div class="filter-buttons">
    <button class="active" onclick="filterSelection('all', this)">All</button>
    <button onclick="filterSelection('nature', this)">Nature</button>
    <button onclick="filterSelection('city', this)">City</button>
    <button onclick="filterSelection('animals', this)">Animals</button>
</div>

<div class="gallery">

<div class="gallery-item nature">
<img src="https://picsum.photos/id/1015/600/400" onclick="openLightbox(0)">
</div>

<div class="gallery-item city">
<img src="https://picsum.photos/id/1011/600/400" onclick="openLightbox(1)">
</div>

<div class="gallery-item animals">
<img src="https://picsum.photos/id/1024/600/400" onclick="openLightbox(2)">
</div>

<div class="gallery-item nature">
<img src="https://picsum.photos/id/1018/600/400" onclick="openLightbox(3)">
</div>

<div class="gallery-item city">
<img src="https://picsum.photos/id/1031/600/400" onclick="openLightbox(4)">
</div>

<div class="gallery-item animals">
<img src="https://picsum.photos/id/237/600/400" onclick="openLightbox(5)">
</div>

</div>

<!-- Lightbox -->
<div class="lightbox" id="lightbox">
<span class="close" onclick="closeLightbox()">&times;</span>
<span class="prev" onclick="changeSlide(-1)">&#10094;</span>
<img id="lightbox-img">
<span class="next" onclick="changeSlide(1)">&#10095;</span>
</div>

<script>
const images = [
"https://picsum.photos/id/1015/600/400",
"https://picsum.photos/id/1011/600/400",
"https://picsum.photos/id/1024/600/400",
"https://picsum.photos/id/1018/600/400",
"https://picsum.photos/id/1031/600/400",
"https://picsum.photos/id/237/600/400"
];

let currentIndex = 0;

function openLightbox(index){
    currentIndex = index;
    document.getElementById("lightbox").style.display="flex";
    document.getElementById("lightbox-img").src=images[currentIndex];
}

function closeLightbox(){
    document.getElementById("lightbox").style.display="none";
}

function changeSlide(step){
    currentIndex += step;

    if(currentIndex < 0)
        currentIndex = images.length - 1;

    if(currentIndex >= images.length)
        currentIndex = 0;

    document.getElementById("lightbox-img").src=images[currentIndex];
}

function filterSelection(category, btn){
    let items = document.getElementsByClassName("gallery-item");
    let buttons = document.querySelectorAll(".filter-buttons button");

    buttons.forEach(button => button.classList.remove("active"));
    btn.classList.add("active");

    for(let i=0; i<items.length; i++){
        if(category=="all"){
            items[i].style.display="block";
        }
        else{
            if(items[i].classList.contains(category))
                items[i].style.display="block";
            else
                items[i].style.display="none";
        }
    }
}
</script>

</body>
</html>
