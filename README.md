# vue-confetti-explosion

> This library is the Vue 3 port of [svelte-confetti-explosion](https://www.npmjs.com/package/svelte-confetti-explosion) which in turn is ported from the [@reonomy/react-confetti-explosion](https://www.npmjs.com/package/@reonomy/react-confetti-explosion) package.

![confetti-large-edit](https://user-images.githubusercontent.com/5460067/111782964-0c6bed80-8890-11eb-8a8b-0a4fdbc30cbd.gif)

## Installing

```bash
# pnpm
pnpm add vue-confetti-explosion

# npm
npm install vue-confetti-explosion

# yarn
yarn add vue-confetti-explosion
```

## Usage

Basic usage:

```html
<script setup>
  import ConfettiExplosion from "vue-confetti-explosion";
</script>

<template>
  <ConfettiExplosion />
</template>
```

Customizing behavior with options:

```html
<ConfettiExplosion :particleCount="200" :force="0.3" />
```

## Props

There's tons of options available for this package. All of them are already documented within the code itself, so you'll never have to leave the code editor.

### particleCount

Number of confetti particles to create.

**type:** `number`

**Default value:** 150

**Example:**

```html
<ConfettiExplosion :particleCount="200" />
```

### particleSize

Size of the confetti particles in pixels

**type:** `number`

**Default value:** 12

**Example:**

```html
<ConfettiExplosion :particleSize="20" />
```

### duration

Duration of the animation in milliseconds

**type:** `number`

**Default value:** 3500

**Example:**

```html
<ConfettiExplosion :duration="5000" />
```

### colors

Colors to use for the confetti particles. Pass string array of colors. Can use hex colors, named colors, CSS Variables, literally anything valid in plain CSS.

**type:** `Array<string>`

**Default value:** `['#FFC700', '#FF0000', '#2E3191', '#41BBC7']`

**Example:**

```html
<ConfettiExplosion :colors=['var(--yellow)', 'var(--red)', '#2E3191', '#41BBC7']
/>
```

### force

Force of the confetti particles. Between 0 and 1. 0 is no force, 1 is maximum force. Will error out if you pass a value outside of this range.

**type:** `number`

**Default value:** 0.5

**Example:**

```html
<ConfettiExplosion :force="0.3" />
```

### stageHeight

Height of the stage in pixels. Confetti will only fall within this height.

**type:** `number`

**Default value:** 800

**Example:**

```html
<ConfettiExplosion :stageHeight="500" />
```

### stageWidth

Width of the stage in pixels. Confetti will only fall within this width.

**type:** `number`

**Default value:** 1600

**Example:**

```html
<ConfettiExplosion :stageWidth="500" />
```

### shouldDestroyAfterDone

Whether or not destroy all confetti nodes after the `duration` period has passed. By default it destroys all nodes, to free up memory.

**type:** `boolean`

**Default value:** `true`

**Example:**

```html
<ConfettiExplosion :shouldDestroyAfterDone="false" />
```

~~## Style Props~~

> This is Svelte specific, still not implemented for this Vue 3 component

~~You can specify two style props on the component: `--x` and `--y`. These will shift the confetti particles on the x and y axis. by how much you specify, These can be in `px`, `em`, `rem`, `vh`, `vw`, literally any valid CSS unit.~~

~~**USAGE:**~~

```html
<ConfettiExplosion --x="10px" --y="10px" />
```

## Examples

```html
<script setup>
  import { nextTick, ref } from "vue";
  import ConfettiExplosion from "vue-confetti-explosion";

  const visible = ref(false);

  const explode = async () => {
    visible.value = false;
    await nextTick();
    visible.value = true;
  };
</script>

<template>
  <div>
    <button @click="explode">Show confetti</button>
    <ConfettiExplosion v-if="visible" />
  </div>
</template>
```

## Potential gotchas

- Your container must be `overflow: visible` in order to allow elements to fully spread across area.
- If your `floorHeight` is too small, particles may visibly land on the floor instead of disappearing off-screen.

## Performance

This library functions by creating 2 DOM nodes for every single confetti. By default, if the `particlesCount` is set to 150, it will create 300 nodes. This is a lot of nodes. For most devices, these many nodes are not a big issue, but I recommend checking your target devices' performance if you choose to go with a higher number, like 400 or 500.

Also, after the specified `duration`, all the confetti DOM nodes will be destroyed. This is to free up memory. If you wish to keep them around, set `shouldDestroyAfterDone` to `false`.

## License

MIT License
© [Valgeir Björnsson](https://valgeir.dev/)
