<script lang="ts">
</script>

<main>
    <form>
        <div class="field">
            <input type="email" name="email" class="input" placeholder=" " />
            <label for="email" class="label">Email</label>
        </div>

        <div class="field">
            <input type="password" name="email" class="input" placeholder=" " />
            <label for="password" class="label">Password</label>
        </div>

        <div class="strength">
            <span class="bar bar-1" />
            <span class="bar bar-2" />
            <span class="bar bar-3" />
            <span class="bar bar-3" />
        </div>

        <ul>
            <li>must be at least 6 characters</li>
            <li>must contain a capital letter</li>
            <li>must contain a number</li>
            <li>must not be forgotten by u</li>
        </ul>
    </form>
</main>

<style>
    form {
        --text-color: #afafaf;
        padding: 10px 300px;
    }
    .field {
        width: 100%;
        margin: 0 auto;
        position: relative;
        border-bottom: 2px dashed var(--text-color);
        margin: 4rem auto 1rem;
        transition: 500ms;
    }
    .label {
        color: var(--text-color);
        font-size: 1.2rem;
    }
    .input {
        outline: none;
        border: none;
        overflow: hidden;
        margin: 0;
        width: 100%;
        padding: 0.25rem 0;
        background: none;
        color: white;
        font-size: 1.2em;
        font-weight: bold;
        transition: border 500ms;
    }
    .input:valid {
        color: yellowgreen;
    }
    .input:invalid {
        color: orangered;
    }
    /* Border animation */
    .field::after {
        content: "";
        position: relative;
        display: block;
        height: 4px;
        width: 100%;
        background: #d16dff;
        transform: scaleX(0);
        transform-origin: 0%;
        opacity: 0;
        transition: all 500ms ease;
        top: 2px;
    }
    .field:focus-within {
        border-color: transparent;
    }
    .field:focus-within::after {
        transform: scaleX(1);
        opacity: 1;
    }
    /* Label animation */
    .label {
        z-index: -1;
        position: absolute;
        transform: translateY(-2rem);
        transform-origin: 0%;
        transition: transform 400ms;
    }
    .field:focus-within .label,
    .input:not(:placeholder-shown) + .label {
        transform: scale(0.8) translateY(-5rem);
        opacity: 1;
    }

    .strength {
        display: flex;
        height: 20px;
        width: 100%;
    }
    .bar {
        margin-right: 5px;
        height: 100%;
        width: 25%;
        transition: box-shadow 500px;
        box-shadow: inset 0px 20px #1f1f1f;
    }
</style>
