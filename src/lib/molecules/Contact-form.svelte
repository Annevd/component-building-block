<form>
    <fieldset>
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

        <textarea id="message" name="message" cols="30" rows="10" placeholder="Typ hier je bericht" required></textarea>
    </fieldset>

    <input type="submit" value="Verzenden"/>
    
</form>