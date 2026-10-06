# Projeto_Integrado_Ciencia_de_Dados

Projeto Integrado — Ciência de Dados
Projeto acadêmico desenvolvido como parte do Projeto Integrado Interdisciplinar de Ciência de Dados, com foco na construção de uma Prova de Conceito (POC) de CRM preditivo para o varejo.
O trabalho integra conceitos de SQL, NoSQL, Data Mining, Machine Learning, Deep Learning e LGPD, demonstrando como diferentes técnicas podem ser combinadas para analisar o comportamento de clientes e apoiar decisões de negócio.

Objetivo
Construir uma POC capaz de:
- Simular dados relacionais de clientes e vendas;
- Simular dados NoSQL de interações de usuários;
- Integrar informações de diferentes fontes;
- Criar métricas de comportamento de clientes;
- Segmentar clientes com K-Means;
- Aplicar Regressão Linear para previsão de gasto;
- Treinar uma pequena Rede Neural para previsão de gasto futuro;
- Gerar documentos simulados no formato utilizado por bancos orientados a documentos;
- Demonstrar práticas de privacidade e minimização de dados alinhadas à LGPD.

Tecnologias utilizadas
- Python
- Google Colab / Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow / Keras
- JSON
- Conceitos de MongoDB / NoSQL

Etapas do projeto
1. Geração dos dados
Foram criadas três bases simuladas:
- Clientes: 100 registros;
- Vendas: 500 registros;
- Interações: 800 registros.
A base de clientes contém informações cadastrais e a base de vendas representa o comportamento de compra. As interações simulam eventos que poderiam ser armazenados em um banco NoSQL, como cliques, buscas, favoritos e adições ao carrinho.

2. Integração SQL simulada
A integração foi realizada com merge() do Pandas, representando uma operação de JOIN entre clientes e vendas por meio da chave id_cliente.
Também foi aplicado um agrupamento equivalente ao GROUP BY do SQL para calcular o valor total gasto por cada cliente.

3. Data Mining e Feature Engineering
Foram criadas três métricas principais:
- gasto_total: soma de todas as compras do cliente;
- num_compras: quantidade de compras realizadas;
- ticket_medio: valor médio gasto por compra.
Essas variáveis foram utilizadas como base para as etapas seguintes do projeto.

4. Clusterização com K-Means
Os clientes foram segmentados em 3 clusters utilizando:
- Gasto total;
- Número de compras;
- Ticket médio.
Os grupos encontrados apresentaram os seguintes perfis médios:
Cluster	Clientes	Gasto médio	Compras médias	Ticket médio
0	51	R$ 1.361,37	3,41	R$ 418,95
1	39	R$ 2.729,37	6,26	R$ 450,28
2	8	R$ 4.534,96	10,25	R$ 456,23


De forma geral:
- Cluster 0: clientes de menor valor e frequência;
- Cluster 1: clientes intermediários;
- Cluster 2: clientes de maior valor e frequência, com potencial para ações de fidelização.

5. Regressão Linear
Foi desenvolvido um modelo de regressão para estimar o gasto total utilizando:
- Idade;
- Renda.
Resultados obtidos:
- R²: aproximadamente -0,0274;
- MAE: aproximadamente R$ 795,10.
Após a padronização das variáveis, a idade apresentou maior contribuição relativa que a renda no modelo gerado.
O baixo desempenho preditivo é coerente com a natureza da base utilizada, pois os dados foram gerados de forma simulada e sem uma relação causal previamente construída entre idade, renda e gasto.

6. Deep Learning
Foi criada uma rede neural do tipo MLP com a seguinte arquitetura:
Entrada: idade + renda
        ↓
Dense(16, ReLU)
        ↓
Dense(8, ReLU)
        ↓
Dense(1)
        ↓
Previsão do gasto
A rede possui 193 parâmetros treináveis e foi utilizada para demonstrar a aplicação de Deep Learning em um problema de regressão.

7. MongoDB simulado e LGPD
Os dados segmentados foram preparados para exportação em JSON, simulando documentos que poderiam ser armazenados em uma coleção MongoDB.
Exemplo:
{
    "id_cliente_anon": "user_1",
    "gasto_total": 2557.3,
    "num_compras": 7,
    "ticket_medio": 365.328571,
    "cluster": 1
}

O identificador original do cliente foi removido e substituído por um identificador alternativo, reduzindo a exposição de dados pessoais.
Essa etapa demonstra principalmente o princípio da necessidade, relacionado à minimização dos dados tratados para a finalidade proposta.
Observação técnica: a substituição de um identificador direto por outro identificador controlado é mais próxima de pseudonimização do que de anonimização irreversível. No contexto acadêmico do projeto, o procedimento foi utilizado para demonstrar a redução da exposição de identificadores pessoais.

Estrutura sugerida do repositório
projeto-integrado-ciencia-de-dados/
│
├── README.md
├── Projeto_Integrado_Ciencia_de_Dados.ipynb
├── clientes_clusters_mongo.json
├── docs/
│   └── Projeto_Integrado_Ciencia_de_Dados_Denis_Pardinho.pdf
└── imagens/
    ├── clusters_kmeans.png
    └── treinamento_rede_neural.png

Como executar
1. Abra o notebook no Google Colab ou Jupyter Notebook;
2. Execute as células na ordem apresentada;
3. Aguarde o treinamento dos modelos;
4. Analise os gráficos e métricas gerados;
5. Ao final, será criado o arquivo clientes_clusters_mongo.json.

Links do projeto
- Repositório GitHub: adicionar aqui o link após a publicação
- Notebook no Google Colab: adicionar aqui o link compartilhável, se desejar
- Relatório acadêmico: adicionar aqui o link do PDF ou arquivo publicado no repositório
O relatório acadêmico também incluirá o link deste repositório GitHub, permitindo acesso ao código-fonte, notebook, resultados e arquivos utilizados no desenvolvimento da atividade.

Contexto acadêmico
Este projeto foi desenvolvido para fins acadêmicos, com dados totalmente simulados. Nenhum dado real de clientes foi utilizado.
O objetivo principal é demonstrar a integração prática de conteúdos estudados em Ciência de Dados, incluindo bancos relacionais e não relacionais, mineração de dados, aprendizado de máquina, redes neurais e privacidade de dados.

Autor
Denis Cassio Pardinho
Curso: Ciência de Dados

Aviso
Este repositório possui finalidade educacional. Os resultados dos modelos não devem ser interpretados como recomendações comerciais reais, pois foram produzidos a partir de dados fictícios e simulados.
Se este projeto estiver sendo visualizado pelo GitHub, os arquivos do notebook e do relatório podem ser acessados diretamente pelas pastas e links disponíveis neste repositório.
