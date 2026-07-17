🚜 CCO Preditivo: Inteligência Artificial na Mineração

Bem-vindo ao repositório do Centro de Controle Operacional (CCO) Preditivo. Este projeto é uma solução avançada de Ciência de Dados desenvolvida para antecipar falhas catastróficas (Alertas 'Don't Go') em frotas de equipamentos pesados de mineração, garantindo a segurança operacional e maximizando o Retorno Sobre Investimento (ROI).

🌐 Acesse o Dashboard Interativo (Streamlit Cloud) Aqui (Insira o seu link gerado no Streamlit Cloud aqui)

🎯 O Problema de Negócio

Nas operações de mineração de alta performance, a disponibilidade física da frota de transporte (caminhões fora de estrada, escavadeiras, etc.) é o motor da rentabilidade.
Quebras não programadas geram um efeito cascata:

Perda total de componentes caríssimos (ex: motor fundido, transmissão destruída).

Paralisação da frente de lavra (perda de produção).

Gargalo na oficina mecânica com manutenções corretivas longas (Downtime).

A Solução: Um sistema de Inteligência Artificial que cruza os dados de apontamentos operacionais com a volumetria de dados de sensores (Telemetria) para detectar a Aceleração da Degradação da máquina, alertando a equipe com 4 horas de antecedência.

⚙️ Arquitetura Técnica e Pipeline de Dados

O projeto foi construído para lidar com desafios clássicos de Big Data e Séries Temporais Industriais:

1. Engenharia de Dados (ETL) e Otimização de Memória

Processamento de gigabytes de dados de telemetria utilizando fastparquet.

Técnicas de Downcasting numérico (64-bits para float32/int8), reduzindo o consumo de memória RAM em mais de 50%.

Sincronização temporal de alta precisão entre ciclos de operação e telemetria usando a função pd.merge_asof (precisão em nanossegundos datetime64[ns]), garantindo alinhamento cronológico estrito e evitando vazamento de dados do futuro (Data Leakage).

2. Engenharia de Features (Aceleração da Degradação)

Em vez de analisar sintomas isolados, o modelo avalia a velocidade com que o equipamento está se deteriorando através de janelas deslizantes (Rolling Windows):

Sintomas_Ultimas_24H / 4H / 2H

Razao_Agravamento_4H e Aceleracao_Aguda_2H: Medem o aumento exponencial de anomalias no componente, simulando a intuição diagnóstica de um mecânico sênior.

3. Modelagem (Machine Learning)

Algoritmo principal: XGBoost Classifier.

Treinamento com validação puramente temporal (passado prevendo o futuro).

Tratamento de classes severamente desbalanceadas através do ajuste estatístico do hiperparâmetro scale_pos_weight.

📊 Resultados e Impacto de Negócio

O verdadeiro valor da solução não está apenas em prever falhas, mas em encontrar o Ponto Ótimo de Operação (Threshold) que equilibra a detecção de problemas com a redução de Falsos Alarmes (que causam paradas preventivas desnecessárias).

No limiar ótimo de 70% de Sensibilidade, a IA em produção projeta:

Filtro de Ruído: Retenção de mais de 1.2 milhão de alertas espúrios de telemetria.

Capital Protegido: Economia de R$ 68.022.000,00 em custos evitados de manutenção corretiva pesada.

Uptime Devolvido: Recuperação de 9.172 horas reais de disponibilidade física para a produção de minério, substituindo quebras longas (média de 24h) por inspeções rápidas (média de 2h).

👨‍💻 Autor

Flayson Santos

Analista de Dados / Arquiteto de Soluções

Projeto desenvolvido como parte do Desafio de Análise Avançada de Dados.

[LinkedIn](https://www.linkedin.com/in/flayson-santos/) | [Portfólio](https://github.com/FlaysonSantos)
