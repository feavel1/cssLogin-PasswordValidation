<script lang="ts">
</script>

<main>
    <form>
        <div class="field">
            <input type="email" name="email" class="input" placeholder="" />
            <label for="email" class="label">Email</label>
        </div>
        <div class="field">
            <input
                type="password"
                name="password"
                class="input"
                placeholder=""
            />
            <label for="password" class="label">Password</label>
        </div>
    </form>
</main>

<style>
    form {
        --text-color: #afafaf;
        max-width: 500px;
    }

    .field {
        width: 100%;
        position: relative;
        border-bottom: 2px dashed var(--text-color);
        margin: 4rem auto 1rem;
    }

    .label {
        color: var(--text-color);
        font-size: 1.2rem;
    }
</style>
