# GitHub Copilot

## Demo Steps

`npm init vue@latest`

...

`npm run dev`

---

Paste

```typescript
import { useWindowSize } from '@vueuse/core'

const { width: windowWidth, height: windowHeight } = useWindowSize()
```

in `HelloWorld.vue`.

---

Then paste

```typescript
// useElementSize
```

below the "useWindowSize" line.

The suggestion after adding a newline should be like:

```typescript
const { width: elementWidth, height: elementHeight } = useElementSize(
  document.body
)
```

Accept it and delete the comment line.

---

Then add a newline immediately after the

```typescript
import { useWindowSize } from '@vueuse/core'
```

from the previous step.

The suggestion should be like:

```typescript
import { useElementSize } from '@vueuse/core'
```

---

Then paste

```typescript
// computed "height" which subtracts
```

and type a `space` and then `w`.

You should see a comment completion suggestion like

```typescript
// computed "height" which subtracts window height from element height
```

which you accept.

Once again you add a newline to see the code suggestion:

```typescript
const height = computed(() => elementHeight.value - windowHeight.value) 
```

After accepting it you delete the comment.

Instead of using the IDE import feature for "computed" error,
go after the last import and type a newline.

You should see a comment completion suggestion like

```typescript
import { computed, defineProps } from 'vue'
```

which you accept, but this must be corrected to

```typescript
import { computed } from 'vue'
```

alone...

---

Delete the

```html
You’ve successfully created a project with
<a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
<a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
```

and press `Ctrl+Enter` to see multiple suggestions in a new tab.

Close the new tab.

Now hover over the suggestions to see the GitHub Copilot command palette for choosing alternative suggestions.

They are impressive but not quite what we want.

Instead, type the word `clipped` until

```html
clipped height: {{ height }}px
```

is suggested.

In the developer tools of your browser, toggle the device toolbar and rotate the device to see the code in action!

---

Now delete the

```typescript
import { useWindowSize } from '@vueuse/core'
```

and the

```typescript
const { width: windowWidth, height: windowHeight } = useWindowSize()
```

and paste

```typescript
const windowHeight = getReactiveWindowHeight()
```

above the `const height`.

Add two newlines after the `useElementSize` to get a suggestion without using `useWindowSize`:

```typescript
const getReactiveWindowHeight = () => {
  const windowHeight = ref(window.innerHeight)
  window.addEventListener('resize', () => {
    windowHeight.value = window.innerHeight
  })
  return windowHeight
}
```

Fix the `ref` error this time with the help of your IDE and rotate the device once again to verify it works...

## There is so much more to come: Copilot X

Copilot X is in technical preview at the moment: <https://github.com/features/preview/copilot-x>

* Copilot is smarter than your IDE coding assistence, but Copilot X is ChatGPT for your IDE!
* Compare the suggestions from `// Serve JSON from a MongoDB` in `mongodb.js`
to GPT-4 to get a glimpse what is about to come!

Optional GPT-4 demo:

* `Example of an anti corruption layer in domain driven design`
* `Synonyms for kind`, `More`, `What is strain in German?`
