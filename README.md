# Manipulando Pixeis com ImageData 

[**Demonstração**: Negativando a Imagem](https://eduardoferr.github.io/trabalhando_pixeis)

<h2 id="The_ImageData_object">O objeto <code>ImageData</code></h2>

<p>o <a href="https://developer.mozilla.org/en-US/docs/Web/API/ImageData" title="The ImageData interface represents the underlying pixel data of an area of a <canvas> element. It is created using the ImageData() constructor or creator methods on the CanvasRenderingContext2D object associated with a canvas: createImageData() and getImageData(). It can also be used to set a part of the canvas by using putImageData()."><code>ImageData</code></a> objeto representa os dados de pixel subjacentes de uma área de um objeto de tela. Ele contém os seguintes atributos somente leitura:</p>

<dl>
 <dt><code>width</code></dt>
 <dd>A largura da imagem em pixels.</dd>
 <dt><code>height</code></dt>
 <dd>A altura da imagem em pixels.</dd>
 <dt><code>data</code></dt>
 <dd>A <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray" title="The Uint8ClampedArray typed array represents an array of 8-bit unsigned integers clamped to 0-255; if you specified a value that is out of the range of [0,255], 0 or 255 will be set instead; if you specify a non-integer, the nearest integer&nbsp;will be set. The contents are initialized to 0. Once established, you can reference elements in the array using the object's methods, or using standard array index syntax (that is, using bracket notation)."><code>Uint8ClampedArray</code></a> representando uma matriz unidimensional contendo os dados na ordem RGBA, com valores inteiros entre 0 e 255 (incluídos).</dd>
</dl>

<p>A propriedade data retorna um Uint8ClampedArray que pode ser acessado para examinar os dados brutos do pixel; Cada pixel é representado por quatro valores de um byte (vermelho, verde, azul e alfa, nessa ordem; isto é, formato "RGBA"). Cada componente de cor é representado por um número inteiro entre 0 e 255. Cada componente recebe um índice consecutivo dentro da matriz, com o componente vermelho do pixel superior esquerdo no índice 0 da matriz. Os pixels seguem da esquerda para a direita e depois para baixo, em todo o array.</p>

>O Uint8ClampedArray contém altura × largura × 4 bytes de dados, com valores de índice variando de 0 a (altura × largura × 4) -1.

<p>Por exemplo, para ler o valor do componente azul do pixel na coluna 200, linha 50 na imagem, você faria o seguinte:</p>
<code>blueComponent = imageData.data[((50 * (imageData.width * 4)) + (200 * 4)) + 2];</code>
