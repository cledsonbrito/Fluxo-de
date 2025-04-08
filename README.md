# Fluxo-de
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Simulador de Fluxo de Caixa - Confecção</title>
</head>
<body>
  <h2>Simulador de Fluxo de Caixa - Confecção Terceirizada</h2>

  <form id="formulario">
    <label>Peças entregues: <input type="number" id="pecas" value="5000"></label><br><br>
    <label>Valor por peça (R$): <input type="number" id="valorPeca" step="0.01" value="2.50"></label><br><br>
    <label>Salários (R$): <input type="number" id="salarios" value="8000"></label><br><br>
    <label>Aluguel (R$): <input type="number" id="aluguel" value="1500"></label><br><br>
    <label>Energia e Água (R$): <input type="number" id="energia" value="1000"></label><br><br>
    <label>Manutenção (R$): <input type="number" id="manutencao" value="500"></label><br><br>
    <label>Retrabalho (%): <input type="number" id="retrabalho" value="5"></label><br><br>
    <label>Custo por retrabalho (R$): <input type="number" id="custoRetrabalho" step="0.01" value="0.30"></label><br><br>
    <label>Outros custos (R$): <input type="number" id="outros" value="700"></label><br><br>

    <button type="button" onclick="calcular()">Calcular</button>
  </form>

  <h3>Resultados:</h3>
  <div id="resultados"></div>

  <script>
    function calcular() {
      const pecas = parseFloat(document.getElementById('pecas').value);
      const valorPeca = parseFloat(document.getElementById('valorPeca').value);
      const salarios = parseFloat(document.getElementById('salarios').value);
      const aluguel = parseFloat(document.getElementById('aluguel').value);
      const energia = parseFloat(document.getElementById('energia').value);
      const manutencao = parseFloat(document.getElementById('manutencao').value);
      const retrabalho = parseFloat(document.getElementById('retrabalho').value);
      const custoRetrabalho = parseFloat(document.getElementById('custoRetrabalho').value);
      const outros = parseFloat(document.getElementById('outros').value);

      const receita = pecas * valorPeca;
      const qtdRetrabalho = pecas * (retrabalho / 100);
      const custoRetrabalhoTotal = qtdRetrabalho * custoRetrabalho;

      const despesas = salarios + aluguel + energia + manutencao + custoRetrabalhoTotal + outros;
      const lucro = receita - despesas;
      const margem = (lucro / receita) * 100;

      document.getElementById('resultados').innerHTML = `
        <p><strong>Receita Bruta:</strong> R$ ${receita.toFixed(2)}</p>
        <p><strong>Despesas Totais:</strong> R$ ${despesas.toFixed(2)}</p>
        <p><strong>Lucro Líquido:</strong> R$ ${lucro.toFixed(2)}</p>
        <p><strong>Margem de Lucro:</strong> ${margem.toFixed(2)}%</p>
      `;
    }
  </script>
</body>
</html>
