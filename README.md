# trabalhando_pixeis
Uma demonstração de como trabalhar pixel a pixel usando o 'ImageData object'
            
                  
                    <div> <div style="text-align: right;" class="prevnext">
    <p><a href="/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations" style="float: left;">« Previous</a><a href="/en-US/docs/Web/API/Canvas_API/Tutorial/Hit_regions_and_accessibility">Next  »</a></p>
</div></div>

<div class="summary">
<p>Até agora não vimos os pixels reais da nossa tela. Com o objeto ImageData, você pode ler e gravar diretamente um array de dados para manipular dados de pixel. Também veremos como a suavização de imagem (anti-aliasing) pode ser controlada e como salvar imagens de sua tela.</p>
</div>

<h2 id="The_ImageData_object">The <code>ImageData</code> object</h2>

<p>o <a href="/en-US/docs/Web/API/ImageData" title="The ImageData interface represents the underlying pixel data of an area of a <canvas> element. It is created using the ImageData() constructor or creator methods on the CanvasRenderingContext2D object associated with a canvas: createImageData() and getImageData(). It can also be used to set a part of the canvas by using putImageData()."><code>ImageData</code></a> objeto representa os dados de pixel subjacentes de uma área de um objeto de tela. Ele contém os seguintes atributos somente leitura:</p>

<dl>
 <dt><code>width</code></dt>
 <dd>A largura da imagem em pixels.</dd>
 <dt><code>height</code></dt>
 <dd>A altura da imagem em pixels.</dd>
 <dt><code>data</code></dt>
 <dd>A <a href="/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8ClampedArray" title="The Uint8ClampedArray typed array represents an array of 8-bit unsigned integers clamped to 0-255; if you specified a value that is out of the range of [0,255], 0 or 255 will be set instead; if you specify a non-integer, the nearest integer&nbsp;will be set. The contents are initialized to 0. Once established, you can reference elements in the array using the object's methods, or using standard array index syntax (that is, using bracket notation)."><code>Uint8ClampedArray</code></a> representando uma matriz unidimensional contendo os dados na ordem RGBA, com valores inteiros entre 0 e 255 (incluídos).</dd>
</dl>

<p>A propriedade data retorna um Uint8ClampedArray que pode ser acessado para examinar os dados brutos do pixel; Cada pixel é representado por quatro valores de um byte (vermelho, verde, azul e alfa, nessa ordem; isto é, formato "RGBA"). Cada componente de cor é representado por um número inteiro entre 0 e 255. Cada componente recebe um índice consecutivo dentro da matriz, com o componente vermelho do pixel superior esquerdo no índice 0 da matriz. Os pixels seguem da esquerda para a direita e depois para baixo, em todo o array.</p>

<p>O Uint8ClampedArray contém altura × largura × 4 bytes de dados, com valores de índice variando de 0 a (altura × largura × 4) -1.</p>

<p>Por exemplo, para ler o valor do componente azul do pixel na coluna 200, linha 50 na imagem, você faria o seguinte:</p>

<pre class="brush: js line-numbers  language-js"><code class=" language-js">blueComponent <span class="token operator">=</span> imageData<span class="token punctuation">.</span>data<span class="token punctuation">[</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token number">50</span> <span class="token operator">*</span> <span class="token punctuation">(</span>imageData<span class="token punctuation">.</span>width <span class="token operator">*</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token punctuation">(</span><span class="token number">200</span> <span class="token operator">*</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token number">2</span><span class="token punctuation">]</span><span class="token punctuation">;</span><span class="line-numbers-rows"><span></span></span></code></pre>
