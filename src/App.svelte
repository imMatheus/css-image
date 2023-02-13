<script lang="ts">
    import konva from 'konva'

    let image: HTMLImageElement
    let image2: HTMLImageElement

    $: {
        if (image) {
            const pixelate = new konva.Image({
                image: image,
                x: 0,
                y: 0,
                width: image.width,
                height: image.height,
                pixelSize: 10,
            })

            console.log(pixelate)

            const layer = new konva.Layer()
            layer.add(pixelate)
            console.log(layer)

            const stage = new konva.Stage({
                container: 'container',
                width: image.width,
                height: image.height,
            })
            stage.add(layer)

            const dataUrl = stage.toDataURL()
            image2.src = dataUrl
        }
    }
</script>

<main>
    <img src="/messi.jpg" alt="" bind:this={image} />
    <img src="" alt="" bind:this={image2} width="200" height="200" />
    <div id="container" />
</main>
