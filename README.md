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
- Uso do Pandas para armazenar os dados coletados em arquivos CSV.

### Dados Coletados:
- IDs dos jogos mais jogados de 2019 a 2024;
- Nomes, preços, gêneros, datas de lançamento e GPUs;
- Análises dos jogos, incluindo o total de positivas, o total de negativas e o total geral;
- Tempo de jogo para terminar história ou para coletar todas as conquistas;
- Pico e média de jogadores jogando simultaneamente dos jogos de 2019 a 2024.

### Sobre os conjuntos de dados:
#### Datasets most_played_2019.csv, most_played_2020.csv, ..., most_played_2024.csv:
Cada dataset representa um ano que vai de 2019 até 2024. E, em cada um dos conjuntos, há os IDs dos jogos mais populares dos respectivos anos, bem como seus picos e médias de jogadores.

1. Processo da Coleta dos Dados: Os IDs foram coletados pelas variações do site da Steam https://store.steampowered.com/charts/mostplayed, como https://store.steampowered.com/charts/bestofyear/bestof2024?tab=3, e, como os respectivos sites utilizam javascript dinâmico, tivemos que coletar, via Scraping, usando ferramentas como Selenium e BeautifulSoup. Também coletamos, do Endpoint https://steamcharts.com/app/ do site da SteamCharts, dados dos números de jogadores, como o pico e a média.

2. Colunas do Dataset:
- id: Identificadores usados pela Steam de cada jogo.
    - Exemplo: "id": 730

- peak: Picos máximos de jogadores jogando simultaneamente de determinado ano.
    - Exemplo: "peak": 767060

- average: Médias do número de jogadores jogando simultaneamente de determinado ano.
    - Exemplo: "average": 669691


#### Dataset all_games_info.csv:
Este conjunto de dados possui informações mais gerais de todos os jogos que estão nos datasets de most_played_{year}.csv, como seus títulos, data de lançamento, gêneros, preços e placas de vídeos com requisitos mínimos para jogar.

1. Processo da Coleta dos Dados: Tivemos que fazer a leitura dos arquivos CSV most_played e, a partir de um Endpoint da Steam https://store.steampowered.com/api/appdetails?, coletar as informações dos jogos, fazendo uma requisição para cada jogo usando seus IDs.

2. Colunas do Dataset:
- id: Identificadores usados pela Steam de cada jogo.
    - Exemplo: "id": 730

- game: Nome dos jogos.
    - Exemplo: "game": Counter-Strike 2

- release_date: Data de lançamento dos jogos.
    - Exemplo: "release_date": "Aug 21, 2012"

- price_USD: Preço, em dolar, dos jogos.
    - Exemplo: "price_USD": 0.0

- genres: Gêneros dos jogos.
    - Exemplo: "genres": "Action, Free To Play"

- pc_requirements: Placas de vídeos atribuidas nos requisitos mínimos de sistema.
    - Exemplo: "pc_requirements": NVIDIAÂ® GeForceÂ® GTX 660 2GB or GTX 1050 2GB / AMD Radeon HD 7850 2GB

#### Dataset all_games_review.csv:
Este dataset tem como informações o score e os números de avaliações, sejam elas positivas ou negativas, que os jogadores deram na plataforma Steam.

1. Processo da Coleta dos Dados: Tivemos que fazer a leitura da coluna dos IDs do arquivo all_games_info.csv e, a partir de um Endpoint da Steam https://store.steampowered.com/appreviews, coletar os números das análises dos jogos por meio de requisições para cada jogo usando seus IDs.

2. Colunas do Dataset:
- id: Identificadores usados pela Steam de cada jogo.
    - Exemplo: "id": 730

- score: pontuação do jogo com base nas análises positivas e negativas.
    - Exemplo: "score": 8

- total_reviews: Número total de análises dos jogadores.
    - Exemplo: "total_reviews": 1351735

- total_positive: Número total de análises positivas dos jogadores.
    - Exemplo: "total_positive": 1161691

- total_negative: Número total de análises negativas dos jogadores.
    - Exemplo: "total_negative": 190044

#### Dataset all_games_time.csv:
Este conjunto de dados tem o tempo de jogo necessário para terminar a história principal ou para coletar todas as conquistas dos jogos.

1. Processo da Coleta dos Dados: Tivemos que fazer a leitura das colunas dos IDs e dos nomes dos jogos ('game') do arquivo all_games_info.csv e, a partir da API HowLongToBeatPy, coletar o tempo de conclusão dos jogos. Entretanto, tivemos que fazer uma normalização nos nomes dos jogos para que houvesse a coleta, e atribuimos algumas excessões ao código.

2. Colunas do Dataset:
- id: Identificadores usados pela Steam de cada jogo.
    - Exemplo: "id": 1245620

- main_story: Tempo médio para terminar história principal dos jogos.
    - Exemplo: "main_story": 59.88

- completionist: Tempo médio para colecionar todas as conquistas dos jogos
    - Exemplo: "completionist": 135.13

### Link para Google Drive contendo os Arquivos CSV: https://drive.google.com/drive/folders/14bGmrpM3Aypa2ZOq5T5ZV_4AojDhR5yS?usp=sharing