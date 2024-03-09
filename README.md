# Modelo-simples-de-intelig-ncia-artificial-utilizando-HTML-PHP-e-JavaScript

Claro, vamos tornar isso um pouco mais complexo adicionando um modelo de aprendizado de máquina simples usando JavaScript e a biblioteca TensorFlow.js. Vou fornecer um exemplo usando um modelo de regressão linear simples.

HTML: Não precisamos mudar muito aqui. Apenas mantenha o formulário como está.

JavaScript: Vamos usar TensorFlow.js para criar e treinar um modelo de regressão linear com alguns dados de exemplo. Este script será responsável por treinar o modelo quando a página for carregada e fazer previsões com base nos dados inseridos pelo usuário.

```javascript
document.addEventListener('DOMContentLoaded', function() {
    // Dados de exemplo para treinamento do modelo
    const inputData = [1, 2, 3, 4];
    const outputData = [2, 4, 6, 8];

    // Definir o modelo de regressão linear
    const model = tf.sequential();
    model.add(tf.layers.dense({ units: 1, inputShape: [1] }));

    // Compilar o modelo
    model.compile({ optimizer: 'sgd', loss: 'meanSquaredError' });

    // Treinar o modelo
    model.fit(tf.tensor2d(inputData, [inputData.length, 1]), tf.tensor2d(outputData, [outputData.length, 1]), { epochs: 100 });

    // Lidar com envio de formulário
    document.getElementById("inputForm").addEventListener("submit", function(event) {
        event.preventDefault();
        let inputData = parseFloat(document.getElementById("inputData").value);

        // Fazer previsão com base nos dados inseridos
        const prediction = model.predict(tf.tensor2d([inputData], [1, 1]));
        const output = prediction.dataSync()[0];
        document.getElementById("output").innerHTML = "Previsão: " + output;
    });
});

```
