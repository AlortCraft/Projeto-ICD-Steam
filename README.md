# Análise de Jogos Populares da Steam

## Integrantes:
- Samuel Santos;
- Pedro Henrique;
- Leonardo Filho;
- Sean Lucas.

## Coleta de Dados
### Abordagens da Coleta de Dados:

- Uso de Scraping por meio de ferramentas como Selenium, BeautifulSoup e Requests em site da Steam que possui javascript dinâmico para a coleta dos IDs dos jogos.
- Uso da API HowLongToBeatPy para coletar dados de tempo de jogo do site HowLongToBeat.
- Uso de Endpoints da Steam e de ferramentas como Requests, json e html, para a coleta de informações gerais dos jogos, incluindo as análises e o pico de jogadores.
- Uso do Pandas para armazenar os dados coletados em arquivos CSV:

### Dados Coletados:
- IDs dos jogos mais jogados de 2019 a 2024;
- Nomes, preços, gêneros, datas de lançamento e GPUs;
- Análises dos jogos, incluindo o total de positivas, o total de negativas e o total geral;
- Tempo de jogo para terminar história ou para coletar todas as conquistas;
- Pico e média de jogadores jogando simultaneamente dos jogos de 2019 a 2024.