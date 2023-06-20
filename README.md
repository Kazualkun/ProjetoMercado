# ProjetoMercado
this is a project that é made for my job, I made this very simple page to show a graphs for the employess of "Supermercado Mairinque" This one shows the porcentage of Sells and Buys from each day, and make a graph to analysis.

o código completo e o acesso é esse:


<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <title>Gráfico de Vendas e Compras</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            padding: 20px;
        }

        h3 {
            color: #000000;
            margin-bottom: 10px;
        }

        input[type="text"] {
            width: 100px;
            padding: 5px;
            margin-right: 10px;
            border: 1px solid #ccc;
            border-radius: 3px;
        }

        div {
            margin-bottom: 20px;
        }

        .date-time {
            background-color: black;
            color: white;
            font-family: Arial, sans-serif;
            padding: 0px;
            font-size: 24px;
            position: absolute;
            top: -25px;
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
            width: 100%;
        }

        .aviso {
            font-family: Arial, sans-serif;
            padding: 0px;
            text-align: center;
            width: 100%;
            font-size: 24px;
        }
    </style>
</head>

<body>
    <p class="date-time"></p>
    <canvas id="chart"></canvas>
    <p class="aviso">os dados são referentes ao dia anterior</p>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            var acougueVendas = parseFloat(document.getElementById('acougue-vendas').value);
            var acougueCompras = parseFloat(document.getElementById('acougue-compras').value);
            var bazarVendas = parseFloat(document.getElementById('bazar-vendas').value);
            var bazarCompras = parseFloat(document.getElementById('bazar-compras').value);
            var bebidasVendas = parseFloat(document.getElementById('bebidas-vendas').value);
            var bebidasCompras = parseFloat(document.getElementById('bebidas-compras').value);
            var congeladosVendas = parseFloat(document.getElementById('congelados-vendas').value);
            var congeladosCompras = parseFloat(document.getElementById('congelados-compras').value);
            var friosVendas = parseFloat(document.getElementById('frios-vendas').value);
            var friosCompras = parseFloat(document.getElementById('frios-compras').value);
            var hortifrutiVendas = parseFloat(document.getElementById('hortifruti-vendas').value);
            var hortifrutiCompras = parseFloat(document.getElementById('hortifruti-compras').value);
            var produtosNaturaisVendas = parseFloat(document.getElementById('produtos-naturais-vendas').value);
            var produtosNaturaisCompras = parseFloat(document.getElementById('produtos-naturais-compras').value);
            var lanchoneteVendas = parseFloat(document.getElementById('lanchonete-vendas').value);
            var lanchoneteCompras = parseFloat(document.getElementById('lanchonete-compras').value);
            var laticiniosVendas = parseFloat(document.getElementById('laticinios-vendas').value);
            var laticiniosCompras = parseFloat(document.getElementById('laticinios-compras').value);
            var limpezaVendas = parseFloat(document.getElementById('limpeza-vendas').value);
            var limpezaCompras = parseFloat(document.getElementById('limpeza-compras').value);
            var merceariaDoceVendas = parseFloat(document.getElementById('mercearia-doce-vendas').value);
            var merceariaDoceCompras = parseFloat(document.getElementById('mercearia-doce-compras').value);
            var merceariaPesadaVendas = parseFloat(document.getElementById('mercearia-pesada-vendas').value);
            var merceariaPesadaCompras = parseFloat(document.getElementById('mercearia-pesada-compras').value);
            var merceariaSalgadaVendas = parseFloat(document.getElementById('mercearia-salgada-vendas').value);
            var merceariaSalgadaCompras = parseFloat(document.getElementById('mercearia-salgada-compras').value);
            var padariaVendas = parseFloat(document.getElementById('padaria-vendas').value);
            var padariaCompras = parseFloat(document.getElementById('padaria-compras').value);
            var peixariaVendas = parseFloat(document.getElementById('peixaria-vendas').value);
            var peixariaCompras = parseFloat(document.getElementById('peixaria-compras').value);
            var perfumariaVendas = parseFloat(document.getElementById('perfumaria-vendas').value);
            var perfumariaCompras = parseFloat(document.getElementById('perfumaria-compras').value);
            var petshopVendas = parseFloat(document.getElementById('petshop-vendas').value);
            var petshopCompras = parseFloat(document.getElementById('petshop-compras').value);
            var rotisseriaCeciliaVendas = parseFloat(document.getElementById('rotisseria-cecilia-vendas').value);
            var rotisseriaCeciliaCompras = parseFloat(document.getElementById('rotisseria-cecilia-compras').value);
            var casaDoNorteVendas = parseFloat(document.getElementById('casa-do-norte-vendas').value);
            var casaDoNorteCompras = parseFloat(document.getElementById('casa-do-norte-compras').value);
            var totalVendas = parseFloat(document.getElementById('total-vendas').value);
            var totalCompras = parseFloat(document.getElementById('total-compras').value);

            // Adicione o ouvinte de evento para o botão
            var adicionarDadosBtn = document.getElementById('adicionar-dados-btn');
            adicionarDadosBtn.addEventListener('click', adicionarDadosAoGrafico);

            function adicionarDadosAoGrafico() {
                var acougueVendas = parseFloat(document.getElementById('acougue-vendas').value);
                var acougueCompras = parseFloat(document.getElementById('acougue-compras').value);
                var bazarVendas = parseFloat(document.getElementById('bazar-vendas').value);
                var bazarCompras = parseFloat(document.getElementById('bazar-compras').value);
                var bebidasVendas = parseFloat(document.getElementById('bebidas-vendas').value);
                var bebidasCompras = parseFloat(document.getElementById('bebidas-compras').value);
                var congeladosVendas = parseFloat(document.getElementById('congelados-vendas').value);
                var congeladosCompras = parseFloat(document.getElementById('congelados-compras').value);
                var friosVendas = parseFloat(document.getElementById('frios-vendas').value);
                var friosCompras = parseFloat(document.getElementById('frios-compras').value);
                var hortifrutiVendas = parseFloat(document.getElementById('hortifruti-vendas').value);
                var hortifrutiCompras = parseFloat(document.getElementById('hortifruti-compras').value);
                var produtosNaturaisVendas = parseFloat(document.getElementById('produtos-naturais-vendas').value);
                var produtosNaturaisCompras = parseFloat(document.getElementById('produtos-naturais-compras').value);
                var lanchoneteVendas = parseFloat(document.getElementById('lanchonete-vendas').value);
                var lanchoneteCompras = parseFloat(document.getElementById('lanchonete-compras').value);
                var laticiniosVendas = parseFloat(document.getElementById('laticinios-vendas').value);
                var laticiniosCompras = parseFloat(document.getElementById('laticinios-compras').value);
                var limpezaVendas = parseFloat(document.getElementById('limpeza-vendas').value);
                var limpezaCompras = parseFloat(document.getElementById('limpeza-compras').value);
                var merceariaDoceVendas = parseFloat(document.getElementById('mercearia-doce-vendas').value);
                var merceariaDoceCompras = parseFloat(document.getElementById('mercearia-doce-compras').value);
                var merceariaPesadaVendas = parseFloat(document.getElementById('mercearia-pesada-vendas').value);
                var merceariaPesadaCompras = parseFloat(document.getElementById('mercearia-pesada-compras').value);
                var merceariaSalgadaVendas = parseFloat(document.getElementById('mercearia-salgada-vendas').value);
                var merceariaSalgadaCompras = parseFloat(document.getElementById('mercearia-salgada-compras').value);
                var padariaVendas = parseFloat(document.getElementById('padaria-vendas').value);
                var padariaCompras = parseFloat(document.getElementById('padaria-compras').value);
                var peixariaVendas = parseFloat(document.getElementById('peixaria-vendas').value);
                var peixariaCompras = parseFloat(document.getElementById('peixaria-compras').value);
                var perfumariaVendas = parseFloat(document.getElementById('perfumaria-vendas').value);
                var perfumariaCompras = parseFloat(document.getElementById('perfumaria-compras').value);
                var petshopVendas = parseFloat(document.getElementById('petshop-vendas').value);
                var petshopCompras = parseFloat(document.getElementById('petshop-compras').value);
                var rotisseriaCeciliaVendas = parseFloat(document.getElementById('rotisseria-cecilia-vendas').value);
                var rotisseriaCeciliaCompras = parseFloat(document.getElementById('rotisseria-cecilia-compras').value);
                var casaDoNorteVendas = parseFloat(document.getElementById('casa-do-norte-vendas').value);
                var casaDoNorteCompras = parseFloat(document.getElementById('casa-do-norte-compras').value);
                var totalVendas = parseFloat(document.getElementById('total-vendas').value);
                var totalCompras = parseFloat(document.getElementById('total-compras').value);


                // Atualize os dados do gráfico
                chart.data.datasets[0].data = [
                    acougueVendas,
                    bazarVendas,
                    bebidasVendas,
                    congeladosVendas,
                    friosVendas,
                    hortifrutiVendas,
                    produtosNaturaisVendas,
                    lanchoneteVendas,
                    laticiniosVendas,
                    limpezaVendas,
                    merceariaDoceVendas,
                    merceariaPesadaVendas,
                    merceariaSalgadaVendas,
                    padariaVendas,
                    peixariaVendas,
                    perfumariaVendas,
                    petshopVendas,
                    rotisseriaCeciliaVendas,
                    casaDoNorteVendas,
                    totalVendas
                ]
                chart.data.datasets[1].data = [
                    acougueCompras,
                    bazarCompras,
                    bebidasCompras,
                    congeladosCompras,
                    friosCompras,
                    hortifrutiCompras,
                    produtosNaturaisCompras,
                    lanchoneteCompras,
                    laticiniosCompras,
                    limpezaCompras,
                    merceariaDoceCompras,
                    merceariaPesadaCompras,
                    merceariaSalgadaCompras,
                    padariaCompras,
                    peixariaCompras,
                    perfumariaCompras,
                    petshopCompras,
                    rotisseriaCeciliaCompras,
                    casaDoNorteCompras,
                    totalCompras
                ]
                // Redesenhe o gráfico
                chart.update();
            }

            var ctx = document.getElementById('chart').getContext('2d');
            var chart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: [
                        'AÇOUGUE',
                        'BAZAR',
                        'BEBIDAS',
                        'CONGELADOS',
                        'FRIOS',
                        'HORTIFRUTI',
                        'PRODUTOS NATURAIS',
                        'LANCHONETE',
                        'LATICÍNIOS',
                        'LIMPEZA',
                        'MERCEARIA DOCE',
                        'MERCEARIA PESADA',
                        'MERCEARIA SALGADA',
                        'PADARIA',
                        'PEIXARIA',
                        'PERFUMARIA',
                        'PETSHOP',
                        'ROTISSERIA CECÍLIA',
                        'CASA DO NORTE',
                        'Total',
                    ],
                    datasets: [{
                        label: 'Vendas',
                        backgroundColor: '#00008b',
                        borderColor: '#00008b',
                        borderWidth: 1,
                        data: [
                            acougueVendas,
                            bazarVendas,
                            bebidasVendas,
                            congeladosVendas,
                            friosVendas,
                            hortifrutiVendas,
                            produtosNaturaisVendas,
                            lanchoneteVendas,
                            laticiniosVendas,
                            limpezaVendas,
                            merceariaDoceVendas,
                            merceariaPesadaVendas,
                            merceariaSalgadaVendas,
                            padariaVendas,
                            peixariaVendas,
                            perfumariaVendas,
                            petshopVendas,
                            rotisseriaCeciliaVendas,
                            casaDoNorteVendas,
                            totalVendas
                        ]
                    }, {
                        label: 'Compras',
                        backgroundColor: '#f30002',
                        borderColor: '#f30002',
                        borderWidth: 1,
                        data: [
                            acougueCompras,
                            bazarCompras,
                            bebidasCompras,
                            congeladosCompras,
                            friosCompras,
                            hortifrutiCompras,
                            produtosNaturaisCompras,
                            lanchoneteCompras,
                            laticiniosCompras,
                            limpezaCompras,
                            merceariaDoceCompras,
                            merceariaPesadaCompras,
                            merceariaSalgadaCompras,
                            padariaCompras,
                            peixariaCompras,
                            perfumariaCompras,
                            petshopCompras,
                            rotisseriaCeciliaCompras,
                            casaDoNorteCompras,
                            totalCompras
                        ]
                    }]
                },
                options: {
                    responsive: true,
                    scales: {
                        y: {
                            beginAtZero: true,
                            max: 200,
                            ticks: {
                                callback: function (value) {
                                    return value + '%';
                                }
                            }
                        }
                    }
                }
            });
        });
    </script>
    <script>


    </script>

    <script>
        function getCurrentDateTime() {
            var now = new Date();
            var date = now.toLocaleDateString('pt-BR');
            var time = now.toLocaleTimeString('pt-BR');
            return date + ' ' + time;
        }

        function updateDateTime() {
            var dateTimeElements = document.getElementsByClassName('date-time');
            var currentDateTime = getCurrentDateTime();

            for (var i = 0; i < dateTimeElements.length; i++) {
                var element = dateTimeElements[i];
                element.textContent = currentDateTime;
            }
        }

        setInterval(updateDateTime, 1000);
    </script>
    <div>
        <h3>AÇOUGUE</h3>
        Vendas: <input type="text" id="acougue-vendas" value="0">
        Compras: <input type="text" id="acougue-compras" value="0">
    </div>
    <div>
        <h3>BAZAR</h3>
        Vendas: <input type="text" id="bazar-vendas" value="0">
        Compras: <input type="text" id="bazar-compras" value="0">
    </div>
    <div>
        <h3>BEBIDAS</h3>
        Vendas: <input type="text" id="bebidas-vendas" value="0">
        Compras: <input type="text" id="bebidas-compras" value="0">
    </div>
    <div>
        <h3>CONGELADOS</h3>
        Vendas: <input type="text" id="congelados-vendas" value="0">
        Compras: <input type="text" id="congelados-compras" value="0">
    </div>
    <div>
        <h3>FRIOS</h3>
        Vendas: <input type="text" id="frios-vendas" value="0">
        Compras: <input type="text" id="frios-compras" value="0">
    </div>
    <div>
        <h3>HORTIFRUTI</h3>
        Vendas: <input type="text" id="hortifruti-vendas" value="0">
        Compras: <input type="text" id="hortifruti-compras" value="0">
    </div>
    <div>
        <h3>PRODUTOS NATURAIS</h3>
        Vendas: <input type="text" id="produtos-naturais-vendas" value="0">
        Compras: <input type="text" id="produtos-naturais-compras" value="0">
    </div>
    <div>
        <h3>LANCHONETE</h3>
        Vendas: <input type="text" id="lanchonete-vendas" value="0">
        Compras: <input type="text" id="lanchonete-compras" value="0">
    </div>
    <div>
        <h3>LATICÍNIOS</h3>
        Vendas: <input type="text" id="laticinios-vendas" value="0">
        Compras: <input type="text" id="laticinios-compras" value="0">
    </div>
    <div>
        <h3>LIMPEZA</h3>
        Vendas: <input type="text" id="limpeza-vendas" value="0">
        Compras: <input type="text" id="limpeza-compras" value="0">
    </div>
    <div>
        <h3>MERCEARIA DOCE</h3>
        Vendas: <input type="text" id="mercearia-doce-vendas" value="0">
        Compras: <input type="text" id="mercearia-doce-compras" value="0">
    </div>
    <div>
        <h3>MERCEARIA PESADA</h3>
        Vendas: <input type="text" id="mercearia-pesada-vendas" value="0">
        Compras: <input type="text" id="mercearia-pesada-compras" value="0">
    </div>
    <div>
        <h3>MERCEARIA SALGADA</h3>
        Vendas: <input type="text" id="mercearia-salgada-vendas" value="0">
        Compras: <input type="text" id="mercearia-salgada-compras" value="0">
    </div>
    <div>
        <h3>PADARIA</h3>
        Vendas: <input type="text" id="padaria-vendas" value="0">
        Compras: <input type="text" id="padaria-compras" value="0">
    </div>
    <div>
        <h3>PEIXARIA</h3>
        Vendas: <input type="text" id="peixaria-vendas" value="0">
        Compras: <input type="text" id="peixaria-compras" value="0">
    </div>
    <div>
        <h3>PERFUMARIA</h3>
        Vendas: <input type="text" id="perfumaria-vendas" value="0">
        Compras: <input type="text" id="perfumaria-compras" value="0">
    </div>
    <div>
        <h3>PETSHOP</h3>
        Vendas: <input type="text" id="petshop-vendas" value="0">
        Compras: <input type="text" id="petshop-compras" value="0">
    </div>
    <div>
        <h3>ROTISSERIA CECÍLIA</h3>
        Vendas: <input type="text" id="rotisseria-cecilia-vendas" value="0">
        Compras: <input type="text" id="rotisseria-cecilia-compras" value="0">
    </div>
    <div>
        <h3>CASA DO NORTE</h3>
        Vendas: <input type="text" id="casa-do-norte-vendas" value="0">
        Compras: <input type="text" id="casa-do-norte-compras" value="0">
    </div>
    <div>
        <h3>Total</h3>
        Vendas: <input type="text" id="total-vendas" value="0">
        Compras: <input type="text" id="total-compras" value="0">
    </div>
    <div>
        <button id="adicionar-dados-btn">Adicionar Dados ao Gráfico</button>
    </div>


</body>

</html>



Esse código foi feito no dia 18/06/2023


a funcionalidade é bem simples o arquivo pronto está adicionado a brench.
