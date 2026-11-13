# Análise Financeira com Python — ClearBank

Projeto desenvolvido como atividade acadêmica da pós-graduação em **Inteligência Artificial e Automação da Rocketseat**. O objetivo é processar um conjunto fictício de transações financeiras, validar os registros e gerar um relatório mensal usando Python.

## Funcionalidades

- Leitura de transações em CSV com `csv.DictReader`.
- Validação de identificador, cliente, data, tipo e valor das transações, além da verificação de campos preenchidos.
- Separação entre registros válidos e inválidos.
- Identificação da primeira e da última data e cálculo do intervalo em dias.
- Agrupamento por mês e cálculo de quantidade, créditos, débitos, saldo, média, maior e menor valor.
- Identificação de transações com valor **superior a R$ 10.000,00** para análise.
- Exibição do relatório no notebook com valores formatados em reais.
- Exportação dos resultados para `relatorio.json`.
- Testes de entradas inválidas, campos ausentes, arquivo inexistente e arquivo vazio.

## Tecnologias

- Python 3.10 ou superior
- Jupyter Notebook (`.ipynb`), executado no VS Code ou em outro ambiente compatível
- Bibliotecas da própria linguagem: `csv`, `json`, `datetime`, `pathlib` e `tempfile`

O processamento principal utiliza a biblioteca padrão do Python, sem necessidade de instalar pandas.

## Estrutura do projeto

```text
clearbank-analise/
├── desafio-final-revisado.ipynb  # Notebook com implementação e testes
├── transacoes.csv               # Dados fictícios de entrada
├── relatorio.json               # Relatório gerado ao executar o notebook
└── README.md                    # Documentação
```

> Se o notebook for renomeado para `desafio-final.ipynb` antes da publicação, atualize o nome na estrutura acima.

## Como executar

1. Tenha o **Python 3.10+** instalado e um ambiente capaz de executar notebooks Jupyter (por exemplo, VS Code com as extensões Python e Jupyter).
2. Abra a pasta do projeto no VS Code.
3. Mantenha `transacoes.csv` na mesma pasta de trabalho em que o notebook é executado.
4. Abra `desafio-final-revisado.ipynb` e selecione um kernel Python.
5. Reinicie o kernel e clique em **Run All** para executar as células na ordem.
6. Confira o relatório exibido e o arquivo `relatorio.json` criado na pasta de execução.
7. Salve o notebook **com as saídas das células**, para que os resultados possam ser visualizados no GitHub.

## Formato dos dados

O arquivo `transacoes.csv` utiliza as colunas:

```csv
id,data,cliente_id,tipo,valor,descricao,categoria
1,2026-01-05,CLI001,credito,3500.00,Salario janeiro,salario
2,2026-01-12,CLI002,debito,180.50,Supermercado,compra
```

As datas seguem `AAAA-MM-DD`, o tipo deve ser `credito` ou `debito` e o valor precisa ser numérico, positivo e finito. A versão atual da validação também exige que todos os campos listados estejam presentes e preenchidos.

## Resultados com a massa de dados utilizada

A massa de exemplo contém **20 transações**, distribuídas entre janeiro e março de 2026: **15 válidas** e **5 inválidas**. Duas transações possuem valores superiores a R$ 10.000,00.

| Mês | Transações válidas | Créditos | Débitos | Saldo |
|---|---:|---:|---:|---:|
| 2026-01 | 5 | R$ 4.700,00 | R$ 520,40 | R$ 4.179,60 |
| 2026-02 | 5 | R$ 18.500,00 | R$ 890,00 | R$ 17.610,00 |
| 2026-03 | 5 | R$ 16.000,00 | R$ 1.009,90 | R$ 14.990,10 |

- **Período analisado:** 05/01/2026 a 25/03/2026 (79 dias).
- **Transações sinalizadas:** ID 7 (R$ 15.000,00) e ID 12 (R$ 12.500,00).

O critério de valor elevado é um **indicador para revisão**, não uma confirmação de fraude.

## Tratamento de erros e testes

O notebook demonstra a rejeição de registros incompletos ou com valores inválidos (`abc`, negativos, zero, `NaN` e infinito). Também testa a leitura de um arquivo inexistente e de um CSV vazio, sem interromper a execução de forma inesperada.

## Arquivo de saída

O `relatorio.json` contém data de geração, totais de registros válidos e inválidos, período analisado, resumo mensal e lista de transações sinalizadas.

## Observações

Os dados utilizados são **fictícios**, criados para fins de aprendizagem. O projeto não acessa contas bancárias reais e não realiza operações financeiras.
