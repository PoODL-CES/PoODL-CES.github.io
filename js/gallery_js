/* =========================================================
   PoODL GALLERY
========================================================= */


/*
    ========================================================
    ADD YOUR PHOTOS HERE
    ========================================================

    To add another photograph, simply copy an entry and
    change the image URL, title and description.

    Categories:

        meet-the-boss
        conferences
        trips
        lab-dinners
        shenanigans
        wet-lab
        dry-lab
*/


const galleryPhotos = [

    /* =====================================================
       POODL ON A TRIP
    ===================================================== */

    {
        image: "https://raw.githubusercontent.com/PoODL-CES/PoODL-CES.github.io/main/poodl_on_a_trip/poodl_on_a_trip1.jpeg",
        category: "trips",
        title: "PoODL on a Trip",
        description: "PoODL · 2026"
    },

    {
        image: "https://raw.githubusercontent.com/PoODL-CES/PoODL-CES.github.io/main/poodl_on_a_trip/poodl_on_a_trip2.jpeg",
        category: "trips",
        title: "PoODL on a Trip",
        description: "PoODL · 2026"
    },

    {
        image: "https://raw.githubusercontent.com/PoODL-CES/PoODL-CES.github.io/main/poodl_on_a_trip/poodl_trip3.jpeg",
        category: "trips",
        title: "PoODL on a Trip",
        description: "PoODL · 2026"
    },

    {
        image: "https://raw.githubusercontent.com/PoODL-CES/PoODL-CES.github.io/main/poodl_on_a_trip/poodl_trip4.jpeg",
        category: "trips",
        title: "PoODL on a Trip",
        description: "PoODL · 2026"
    },

    {
        image: "https://raw.githubusercontent.com/PoODL-CES/PoODL-CES.github.io/main/poodl_on_a_trip/poodl_trip5.jpeg",
        category: "trips",
        title: "PoODL on a Trip",
        description: "PoODL · 2026"
    }

];


/* =========================================================
   ELEMENTS
========================================================= */

const photoGrid = document.getElementById("photo-grid");

const photoCount = document.getElementById("photo-count");

const emptyGallery = document.getElementById("empty-gallery");

const filterButtons =
    document.querySelectorAll(".filter-btn");


const lightbox =
    document.getElementById("lightbox");

const lightboxImage =
    document.getElementById("lightbox-image");

const lightboxTitle =
    document.getElementById("lightbox-title");

const lightboxDescription =
    document.getElementById("lightbox-description");

const lightboxClose =
    document.getElementById("lightbox-close");

const lightboxPrev =
    document.getElementById("lightbox-prev");

const lightboxNext =
    document.getElementById("lightbox-next");


/* =========================================================
   CURRENT STATE
========================================================= */

let currentFilter = "all";

let visiblePhotos = [];

let currentPhotoIndex = 0;


/* =========================================================
   DISPLAY PHOTOS
========================================================= */

function displayPhotos() {

    photoGrid.innerHTML = "";

    if (currentFilter === "all") {

        visiblePhotos = galleryPhotos;

    } else {

        visiblePhotos = galleryPhotos.filter(
            photo =>
                photo.category === currentFilter
        );

    }


    /* Photo count */

    photoCount.textContent =
        `${visiblePhotos.length} ${
            visiblePhotos.length === 1
                ? "photo"
                : "photos"
        }`;


    /* No photos */

    if (visiblePhotos.length === 0) {

        emptyGallery.style.display = "block";

        return;

    }


    emptyGallery.style.display = "none";


    /* Create photo cards */

    visiblePhotos.forEach(
        (photo, index) => {

            const card =
                document.createElement("article");

            card.className = "photo-card";


            card.innerHTML = `

                <img
                    src="${photo.image}"
                    alt="${photo.title}"
                    loading="lazy"
                >

                <div class="photo-overlay">

                    <h3>
                        ${photo.title}
                    </h3>

                    <p>
                        ${photo.description}
                    </p>

                </div>

            `;


            card.addEventListener(
                "click",
                () => openLightbox(index)
            );


            photoGrid.appendChild(card);

        }
    );

}


/* =========================================================
   FILTERING
========================================================= */

filterButtons.forEach(
    button => {

        button.addEventListener(
            "click",
            () => {

                filterButtons.forEach(
                    btn =>
                        btn.classList.remove("active")
                );


                button.classList.add("active");


                currentFilter =
                    button.dataset.filter;


                displayPhotos();

            }
        );

    }
);


/* =========================================================
   OPEN LIGHTBOX
========================================================= */

function openLightbox(index) {

    currentPhotoIndex = index;

    updateLightbox();

    lightbox.classList.add("open");

    lightbox.setAttribute(
        "aria-hidden",
        "false"
    );

    document.body.style.overflow = "hidden";

}


/* =========================================================
   UPDATE LIGHTBOX
========================================================= */

function updateLightbox() {

    const photo =
        visiblePhotos[currentPhotoIndex];


    if (!photo) {
        return;
    }


    lightboxImage.src =
        photo.image;

    lightboxImage.alt =
        photo.title;

    lightboxTitle.textContent =
        photo.title;

    lightboxDescription.textContent =
        photo.description;

}


/* =========================================================
   CLOSE LIGHTBOX
========================================================= */

function closeLightbox() {

    lightbox.classList.remove("open");

    lightbox.setAttribute(
        "aria-hidden",
        "true"
    );

    document.body.style.overflow = "";

}


/* =========================================================
   NEXT PHOTO
========================================================= */

function nextPhoto() {

    if (visiblePhotos.length === 0) {
        return;
    }


    currentPhotoIndex =
        (currentPhotoIndex + 1)
        % visiblePhotos.length;


    updateLightbox();

}


/* =========================================================
   PREVIOUS PHOTO
========================================================= */

function previousPhoto() {

    if (visiblePhotos.length === 0) {
        return;
    }


    currentPhotoIndex =
        (
            currentPhotoIndex - 1
            + visiblePhotos.length
        )
        % visiblePhotos.length;


    updateLightbox();

}


/* =========================================================
   BUTTON EVENTS
========================================================= */

lightboxClose.addEventListener(
    "click",
    closeLightbox
);


lightboxNext.addEventListener(
    "click",
    nextPhoto
);


lightboxPrev.addEventListener(
    "click",
    previousPhoto
);


/* =========================================================
   CLOSE BY CLICKING BACKGROUND
========================================================= */

lightbox.addEventListener(
    "click",
    event => {

        if (event.target === lightbox) {

            closeLightbox();

        }

    }
);


/* =========================================================
   KEYBOARD CONTROLS
========================================================= */

document.addEventListener(
    "keydown",
    event => {

        if (
            !lightbox.classList.contains("open")
        ) {

            return;

        }


        if (event.key === "Escape") {

            closeLightbox();

        }


        if (event.key === "ArrowRight") {

            nextPhoto();

        }


        if (event.key === "ArrowLeft") {

            previousPhoto();

        }

    }
);


/* =========================================================
   INITIALIZE
========================================================= */

displayPhotos();
