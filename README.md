# Running Svelte SPA on GitHub Pages
Example for how to run a simple Svelte single-page app (SPA) in GitHub pages.

1. Follow the official docs for bundling your SvelteKit project as a static site: https://svelte.dev/docs/kit/adapter-static#GitHub-Pages

2. Make sure you configure your `config.kit.paths.base` to match your repo name if your target page is not equivalent to `<your-username>.github.io`:
    ```js
    const config = {
        ...
        kit: {
            ...
            paths: {
                base: process.argv.includes('dev') ? '' : '/<REPO NAME>'
            },
            ...
        }
        ...
    }
    ```

3. I also did not configure the fallback option.

4. Configure hash-based routing in your config (and update your app to use it as well):
    ```js
    const config = {
        kit: {
            ...
            router: {
                type: "hash"
            },
            ...
        },
        ...
    }
    ```

    ```html
    <script>
        import { goto } from "$app/navigation";
    </script>

    <button onclick={() => goto(`#/page${targetPage}`)}>Goto Page {targetPage}</button>
    ```

5. Add a copy of the `deploy.yml` from the official docs to your repro to trigger the build and deploy whenever you push to the main branch.