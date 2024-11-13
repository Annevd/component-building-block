<form>

    <fieldset class="questions">
        <legend>Reden voor contact:</legend>
            <label for="question">Ik heb een vraag</label>
            <input type="radio" id="question" name="contact-reason" value="question" checked/>

            <label for="workshop">Ik wil mij aanmelden voor een workshop</label>
            <input type="radio" id="workshop" name="contact-reason" value="workshop">
    </fieldset>

    <fieldset>
        <label for="name">Voornaam:</label>
        <input type="text" id="name" name="name" placeholder="Voer je voornaam in" required/>

        <label for="lastname">Achternaam:</label>
        <input type="text" id="lastname" name="lastname" placeholder="Voer je achternaam in" required/>

        <label for="email">E-mail:</label>
        <input type="email" id="email" name="email" placeholder="Voer je e-mailadres in" required/>

        <label for="message">
            Stel je vraag of vertel voor welke workshop je je wilt aanmelden!
        </label>

        <textarea id="message" name="message" cols="30" rows="7" placeholder="Typ hier je bericht" required></textarea>
    </fieldset>

    <input type="submit" value="Verzenden"/>

</form>

<style>

form {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 35rem;
    gap: 1rem;
    color: var(--card-color-green);
    font-family: var(--sub-header-font);
}

fieldset {
    display: flex;
    flex-direction: column;
    border: none;
    gap: 0.5rem;
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
    outline: 1px solid #B37400;
}

input[type='submit'] {
    border-radius: 2rem;
    border: none;
    cursor: not-allowed;
    padding: 0.5rem 1rem;
    margin: 0.5rem 0;
    font-size: 1rem;
    width: 8rem;
    background-color: #657266;
    color: var(--text-color-white);
    transition: ease-in 0.1s;
}

form:valid input[type='submit'] {
    cursor: pointer;
    background: var(--main-color-green);
}

form:valid input[type='submit']:hover {
    background-color: #4A8235;
    transform: scale(1.02);
}

input,
textarea {
    font-family: var(--paragraph-font);
}

::placeholder {
    color: #545454;
}

/* form focus valid  */

input[type='text']:valid,
input[type='email']:valid,
textarea:valid {
    outline: 2px solid var(--card-color-green);
    background: #E8FFE8;
}

input[type='text']:user-invalid,
input[type='email']:user-invalid,
textarea:user-invalid {
    outline: 2px solid var(--invalid-color-red);
    /* background: #FFEFEF; */
}

/* form focus styling */

input[type='text']:focus,
input[type='email']:focus,
textarea:focus {
    outline: 2px solid #B37400;
    background: lightgoldenrodyellow;
}

</style>