<script lang="ts">
    import { current_component } from "svelte/internal";

    let strength = 0;
    let validation = [];
    let showPassword = false;

    function validatePassword(event) {
        const password = event.target.value;

        validation = [
            password.length > 5,
            password.search(/[A-Z]/) > -1,
            password.search(/[0-9]/) > -1,
            password.search(/[!@#$%^&*()_+<>:;?]/) > -1,
        ];

        strength = validation.reduce((acc, cur) => acc + cur);
    }
</script>

<main>
    <form>
        <span>
            <div class="field">
                <input
                    type="email"
                    name="email"
                    class="input"
                    placeholder=" "
                />
                <label for="email" class="label">Email</label>
            </div>

            <div class="field">
                <input
                    type={showPassword ? "text" : "password"}
                    name="email"
                    class="input"
                    placeholder=" "
                    on:input={validatePassword}
                />
                <label for="password" class="label">Password</label>
            </div>
            <span
                class="toggle-password"
                on:mouseenter={() => (showPassword = true)}
                on:mouseleave={() => (showPassword = false)}
            >
                {showPassword ? "🐵" : "🙈"} ⬅ Hover me to show passoword ♡♡♡
            </span>
            <div class="strength">
                <span class="bar bar-1" class:bar-show={strength > 0} />
                <span class="bar bar-2" class:bar-show={strength > 1} />
                <span class="bar bar-3" class:bar-show={strength > 2} />
                <span class="bar bar-4" class:bar-show={strength > 3} />
            </div>

            <ul class="hint-list">
                <li>
                    {validation[0] ? "✅" : "❗️"} must be at least 6 characters
                </li>
                <li>
                    {validation[1] ? "✅" : "❗️"} must contain a capital letter
                </li>
                <li>{validation[2] ? "✅" : "❗️"} must contain a number</li>
                <li>
                    {validation[3] ? "✅" : "❗️"} must have a special char !@#...
                </li>
            </ul>
        </span>
    </form>
</main>

<style>
    form {
        /* --text-color: #afafaf;
        padding: 10px 300px;
        color: white; */
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        min-height: 20px;
        padding: 36px 10%;
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

    .bar-show {
        box-shadow: none;
    }

    .bar-1 {
        background: linear-gradient(to right, red, orangered);
    }
    .bar-2 {
        background: linear-gradient(to right, orangered, orange);
    }
    .bar-3 {
        background: linear-gradient(to right, orange, yellow);
    }
    .bar-4 {
        background: linear-gradient(to right, yellow, yellowgreen);
    }

    .toggle-password {
        color: #afafaf;
        position: flex;
        cursor: help;
        font-size: 1rem;
        right: 0.25rem;
    }
    .hint-list li {
        list-style-type: none;
        color: var(--text-color);
    }
    .hint-list {
        padding: 1px;
    }
</style>
