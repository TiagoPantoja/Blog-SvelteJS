<script>
    import { Link } from "svelte-navigator";
    export let blog;
    let username = "Jane Doe";
    let designation = "B.Sc. in Physics";
    let loved = false;

    const getImageSrc = () => {
      if (blog.id % 2 == 0) {
        return `https://randomuser.me/api/portraits/women/${blog.userId}.jpg`;
      } else {
        return `https://randomuser.me/api/portraits/men/${blog.userId}.jpg`;
      }
    };
    const handleFavourite = () => {
      loved = !loved;
    };
  </script>

  <div class="media d-flex align-items-sm-end flex-column flex-sm-row">
    <div class="d-flex flex-row align-items-end">
      <div class="media-avatar">
        <div class="avatar">
          <img src={getImageSrc()} alt={username} />
        </div>
      </div>
      <div class="d-sm-none">
        <h5 class="mt-0 mb-1">{blog.title}</h5>
        <p class="m-0 text-secondary" style="font-size: 14px;">
          {username}, {designation}
        </p>
      </div>
    </div>
    <div class="media-body mt-2 mt-sm-0">
      <div class="d-none d-sm-block">
        <h5 class="mt-0 mb-1">{blog.title}</h5>
        <p class="m-0 mb-2 text-secondary" style="font-size: 14px;">
          {username}, {designation}
        </p>
      </div>
      <p class="para">
        {blog.body.slice(0, 150)}
        {#if blog.body.length > 150}
          <Link to={`/blog/${blog.id}`}>...See More</Link>
        {/if}
      </p>
      <div class="d-flex align-items-end justify-content-between">
        <button class="btn btn-sm mt-2" style="border: 1px solid lightgray;">
          Share
        </button>
        <span
          title="Add To Favourite"
          style="cursor: pointer; z-index: 0;"
          on:click={handleFavourite}
        >
          <ion-icon
            name={`heart${loved ? "-sharp" : "-outline"}`}
            title="Add To Favourite"
            style="font-size: 24px; pointer-events:none;"
          />
        </span>
      </div>
    </div>
  </div>

  <style>
    .media {
      padding: 1rem;
      box-shadow: 0px 0px 4px lightgray;
      border-radius: 8px;
      margin-top: 1rem;
      background-color: white;
    }
    .avatar {
      width: 64px;
      height: 64px;
      background-color: gray;
      overflow: hidden;
      margin-right: 1rem;
    }
    .avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .para {
      margin-bottom: 0;
      line-height: 1.4rem;
      font-size: 0.95rem;
      word-wrap: break-word;
      word-break: break-all;
    }
  </style>