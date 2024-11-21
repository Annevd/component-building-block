<li>
    <div class="card-container">
        <picture>
            <img height=200 src="/src/lib/assets/workshop.webp" alt="">
        </picture>
        <div class="info-container">
            <h2>Stekjes maken</h2>
            <ul>
                <time datetime="13:00">13:00</time>
                <time datetime="2024-11-03">03/11/2024</time>
                <address>OBA Linnaeusstraat</address>
                <p>€10,-</p>
            </ul>
            <a href="/">Meld je aan <span><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 44 47"><path d="M40.492 18.788 8.942 1.034C4.944-1.218 0 1.673 0 6.262v34.704c0 4.537 4.842 7.433 8.84 5.285l31.549-16.948c4.167-2.239 4.225-8.195.103-10.515Z" fill="#fff"></path></svg></span></a>
        </div>
    </div>
</li>

<style>
/* Base styles */
li {
    list-style: none;
    container-type: inline-size; /* Container query property */
    container-name: card;        /* Container query property */
}

.card-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    height: auto;
    width: auto;
    padding: 1rem;
    background: var(--main-color-beige);
    border-radius: 1rem;
}

/* Layout voor grotere schermen met container queries */

@container card (width > 23rem) {
    .card-container {
        flex-direction: row;
        height: 14rem;
    }
    .card-container picture {
        width: 40%;
    }
    .info-container {
        gap: 0;
    }
    li picture {
        max-height: none;
    }
}

/* Picture & image styles */

li picture,
li img {
    height: 100%;
    width: 100%;
    max-height: 13rem;
    display: block;
}

li img {
    object-fit: cover;
    border-radius: 1rem;
}

/* Info container styles */

.info-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 1rem;
    color: var(--main-color-brown);
}

h2 {
    font-weight: bolder;
}

ul {
    font-weight: bold;
}

time {
    display: block;
}

/* Button styles */

a {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    width: max-content;
    border-radius: 2em;
    padding: 0.2em 0.6em;
    text-decoration: none;
    font-size: 1em;
    background: var(--card-color-green);
    color: var(--text-color-white);
}

a span {
    display: flex;
    align-items: center;
    justify-content: center;
}

a span svg {
    height: 0.75rem;
    width: auto;
}
</style>