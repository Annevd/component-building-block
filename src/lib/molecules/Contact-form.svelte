<script>
    import { onMount } from "svelte";
    let isLoading = false;

    onMount(() => {
        document.querySelector("form").addEventListener("submit", function(event) {
            event.preventDefault(); // Prevent the default form submission

            isLoading = true;

            setTimeout(() => {
                const submitButton = document.querySelector("button[type='submit']");
                submitButton.textContent = "Verzenden gelukt!"; // Change the button text
                isLoading = false; 

                submitButton.disabled = true; 
                submitButton.style.backgroundColor = "var(--main-color-green)";
                submitButton.style.color = "white";

                document.querySelector("form").reset();
            }, 2000);
        });
    });
</script>

<form class="{isLoading ? 'loading-overlay' : ''}">

    <fieldset class="questions">
        <legend>Reden voor contact:</legend>
            <label for="question">Ik heb een vraag</label>
            <input type="radio" id="question" name="contact-reason" value="question" checked/>

            <label for="workshop">Ik wil mij aanmelden voor een workshop</label>
            <input type="radio" id="workshop" name="contact-reason" value="workshop">
    </fieldset>

    <div class="field-container">
        <div>
            <label for="name">Voornaam:</label>
            <input type="text" id="name" name="name" placeholder="Voer je voornaam in*" required/>
        </div>

        <div>
            <label for="lastname">Achternaam:</label>
            <input type="text" id="lastname" name="lastname" placeholder="Voer je achternaam in*" required/>
        </div>

        <div>
            <label for="email">E-mail:</label>
            <input type="email" id="email" name="email" placeholder="Voer je e-mailadres in*" required/>
        </div>

        <label for="message">
            Stel je vraag of vertel voor welke workshop je je wilt aanmelden!
        </label>
        <textarea id="message" name="message" cols="30" rows="7" placeholder="Typ hier je bericht*" required></textarea>
    </div>

    <button type="submit" value="Verzenden" class="{isLoading ? 'loading' : ''}">Verzenden</button>

</form>

<style>

form {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 35rem;
    gap: 1.25rem;
    color: var(--text-color-green);
    font-family: var(--sub-header-font);
}

fieldset {
    display: flex;
    flex-direction: column;
    border: none;
    gap: 0.5rem;
}

.field-container {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

legend {
    padding: 0.5rem 0;
}

.questions {
    display: grid;
    grid-template-columns: 1.5rem auto;
    grid-template-areas:
    'radio1 question1'
    'radio2 question2';
}

.questions input:first-of-type {
    grid-area: radio1;
}

.questions input:nth-of-type(2) {
    grid-area: radio2;
}

.questions label:first-of-type {
    grid-area: question1;
}

.questions label:nth-of-type(2) {
    grid-area: question2;
}

input[type='radio']{
    width: 1.5rem;
    height: 1.5rem;
    accent-color: var(--main-color-green);
    cursor: pointer;
}

input[type='text'],
input[type='email'],
textarea {
    border: none;
    padding: 0.5rem;
    border-radius: var(--border-card);
    outline: none;
    /* box-shadow: 0px 2px 4px hsl(32 37% 39% / 1); */
    outline: 1px solid var(--input-border-color);
    position: relative;
    z-index: 100;
}

button[type='submit'] {
    border-radius: 2rem;
    border: none;
    padding: 0.5rem 1rem;
    margin: 0.5rem 0;
    font-size: 1rem;
    width: fit-content;
    background-color: #657266;
    color: var(--text-color-white);
    transition: ease-in 0.1s;
}

/* Loading cursor state */

.loading-overlay {
    position: relative;
}

.loading-overlay::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    cursor: wait;
    z-index: 100;
}

/* Submit button after valid form  */

form:valid button[type='submit'] {
    cursor: pointer;
    background: var(--main-color-green);
}

form:valid button[type='submit']:hover {
    background-color: #4A8235;
    transform: scale(1.02);
}

input,
textarea,
button {
    font-family: var(--paragraph-font);
}

::placeholder {
    color: #545454;
}

/* form focus styling */

input[type='text']:focus,
input[type='email']:focus,
textarea:focus {
    outline: 2px solid #B37400;
    background: lightgoldenrodyellow;
}

/* form focus valid  */

input[type='text']:valid,
input[type='email']:valid,
textarea:valid {
    outline: 2px solid var(--valid-color-green);
    background: #E8FFE8;
}

/* form focus invalid */

input[type='text']:user-invalid,
input[type='email']:user-invalid,
textarea:user-invalid {
    outline: 2px solid var(--invalid-color-red);
    /* background: #FFEFEF; */
}

/* Form animated valid styling */

div {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    position: relative;
}

.field-container div::after {
    content: "";
    position: absolute;
    top: -0.15rem;
    right: 10px;
    width: 40px;
    height: 40px;
    scale: 0.5;
    background-image: url('/assets/plant.svg');
    background-size: contain;
    background-repeat: no-repeat;
    opacity: 0;
    z-index: 10;
    transform: translateY(100%);
    transition: all 0.5s cubic-bezier(.75,-0.5,0,1.75);
}

/* Loading state submit button animation */

@keyframes pulse {
    50% {
        transform: scale(1.025);
    }
    100% {
        transform: scale(1);
    }
}

@media (prefers-reduced-motion: no-preference) {

    /* Plant valid animation */

    .field-container div:has(input:valid)::after {
        opacity: 1;
        scale: 1;
        transform: translateY(0);
    }

    .field-container div:has(input:focus)::after,
    .field-container div:has(input:focus:valid)::after {
        transform: translateY(20%);
        opacity:1;
        scale: 1;
        transition-delay: .3s;
    }

    /* Loading animation submit button */

    button[type='submit'].loading {
        animation: pulse 0.8s infinite;
        cursor: wait; 
    }
}

</style>