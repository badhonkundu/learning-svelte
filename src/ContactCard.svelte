<script>
    export let userName;
    export let jobTitle;
    export let description;
    export let imgUrl =
        "https://media-exp1.licdn.com/dms/image/C4E03AQHYMGnZBWQ50g/profile-displayphoto-shrink_400_400/0?e=1609977600&v=beta&t=8Yu5ZtuvdinF9VuyMXuJC9_iWc0PNQSUBYQjW9fu5VU";
</script>

<style>
    .contact-card {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        max-width: 30rem;
        border-radius: 5px;
        margin: 1rem 0;
    }

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 7rem;
    }

    .thumb {
        width: 33%;
        height: 100%;
    }

    .thumb-placeholder {
        background-color: #ccc;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .user-data {
        width: 67%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding-left: 1rem;
    }

    h1 {
        font-size: 1.25rem;
        font-family: "Roboto Slab", sans-serif;
        margin: 0.5rem 0;
    }

    h2 {
        font-size: 1rem;
        font-weight: normal;
        color: #5a5a5a;
        margin: 0;
        margin-bottom: 0.5rem;
    }

    .description {
        border-top: 1px solid #ccc;
        padding: 1rem;
    }
</style>

<div class="contact-card">
    <header>
        <div class="thumb" class:thumb-placeholder={!imgUrl}>
            <img src={imgUrl} alt="Photo of {userName}" />
        </div>
        <div class="user-data">
            <h1>{userName}</h1>
            <h2>{jobTitle}</h2>
        </div>
    </header>
    <div class="description">
        <!--
            Commneted example here the description prop can be sent as hml and this would dislay html.
            By default svete renders html as normal text
            MAKE SURE TO SANITIZE INPUT DATA IF YOU NEED TO USE THIS
            {@html description}
        -->
        <p>{description}</p>
    </div>
</div>
