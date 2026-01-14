# ☁️ AWS Architecture: Otimização de Custos e Performance
Projeto desenvolvido como parte do Bootcamp Santander 2025 - Ciência de Dados com Python da DIO.

#### 📝 Descrição do Desafio
O desafio consiste em apresentar o uso de 3 serviços AWS para compor a implementação de serviços em cloud, para uma empresa farmaceutica em expansão, de modo a diminuir custos.

#### 🛠️ Serviços EscolhidosAbaixo, detalho as ferramentas selecionadas para compor esta solução estratégica:
1. Amazon S3 Intelligent-TieringCategoria: Armazenamento de Objetos (Storage) 
   O que é: Uma classe de armazenamento do Amazon S3 que move automaticamente os dados entre camadas de acesso (frequente, infrequente, arquivo) com base no uso real.
   Por que foi escolhido:Em projetos de Data Science, lidamos com grandes volumes de dados (Data Lakes). Alguns dados são acessados todo dia, outros raramente.
   O Intelligent-Tiering elimina a necessidade de criar scripts complexos de ciclo de vida. Ele monitora os padrões de acesso e move os objetos para a camada mais barata automaticamente, gerando economia de custos sem impacto operacional.

2. Amazon DynamoDBCategoria: Banco de Dados (NoSQL)
   O que é: Um serviço de banco de dados NoSQL chave-valor e documento, totalmente gerenciado, que oferece desempenho rápido e previsível com escalabilidade contínua.
   Por que foi escolhido:Ideal para armazenar metadados, logs de aplicações ou dados não estruturados que exigem alta disponibilidade.
   Por ser Serverless, não precisamos gerenciar servidores, permitindo focar na análise dos dados e não na infraestrutura.

3. Amazon DynamoDB Accelerator (DAX)Categoria: Caching (Performance)
   O que é: Um cache na memória totalmente gerenciado e altamente disponível para o Amazon DynamoDB.
   Por que foi escolhido:Para cenários de Data Intensive (uso intensivo de dados), apenas o banco de dados pode não ser suficiente para leituras massivas.
   O DAX aumenta a performance de leitura de milissegundos para microssegundos, aliviando a carga no banco principal e entregando dados em tempo real para dashboards ou modelos de Machine Learning.

  
 #### 📊 Arquitetura Proposta (Fluxo Conceitual)
 Embora este projeto seja focado na escolha das ferramentas, o fluxo de dados idealizado seria:
 Ingestão: Dados brutos (imagens, logs, CSVs) são salvos no S3 Intelligent-Tiering.
 Processamento: Metadados desses arquivos ou resultados de análises rápidas são gravados no DynamoDB.
 Consumo: Aplicações de consulta ou Dashboards acessam esses dados através do DAX para garantir velocidade extrema, sem sobrecarregar o banco.


 #### 🚀 Benefícios da Solução
 - Custo
 O S3 Intelligent-Tiering garante que não pagaremos caro por dados que ninguém está acessando.
 - Performance
 O DAX garante respostas imediatas, essencial para experiência do usuário e apps em tempo real.
 - Escalabilidade
 O DynamoDB ajusta a capacidade conforme a demanda de tráfego aumenta ou diminui.


 
#### 📚 Referências

[Documentação Oficial Amazon S3 Intelligent-Tiering](https://aws.amazon.com/pt/s3/storage-classes/intelligent-tiering/)<br>
[Documentação Oficial Amazon DynamoDB](https://aws.amazon.com/pt/dynamodb/)<br>
[Documentação Oficial Amazon DAX](https://aws.amazon.com/pt/dynamodbaccelerator/)
