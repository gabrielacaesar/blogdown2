---
title: "Recomendações de melhoria nos dados do TSE"
author: "Gabriela Caesar"
date: "2020-12-02"
output: html_document
slug: 2020-12-02-recomendacoes-de-melhoria-nos-dados-do-tse
categories: [dados abertos]
tags: [dados abertos, tse, eleições]
---

No início das eleições, eu comecei a escrever uma lista das melhorias que o TSE poderia fazer nos dados.                
Depois de quase dois meses, a lista tem 30 itens.                
[Joguei a lista no Twitter](https://twitter.com/gabrielacaesar/status/1333857054700744705) e outras pessoas contribuíram com mais sugestões.               
E eu me lembrei de outras sugestões.               

O arquivo final foi enviado para a estatística e a assessoria de imprensa do TSE.               
Também mandei tudo para a Ouvidoria do TSE como sugestão.               
Protocolos: 44906302133054, 44906502133437, 44906602133702 e 44906702133958.               


SUGESTÕES DE MELHORIAS AOS DADOS DO TSE                
Lista de melhorias para os dados do Tribunal Superior Eleitoral (TSE) feita após o uso diário na cobertura eleitoral de 2020.                
Também foram recebidas contribuições de outros profissionais [https://twitter.com/gabrielacaesar/status/1333857054700744705].                

Recomendações gerais:                
1) TSE deve criar um Plano de Dados Abertos e torná-lo público, após considerar demandas via LAI e também demandas de consulta pública para ouvir a população, incluindo principalmente jornalistas e programadores;                
2) Plano de Dados Abertos deve ter prazos e nomes de bases de dados a serem abertas;                
3) Nova base de dados deve reunir e-mail e telefone de contato de todos os diretórios estaduais e municipais dos partidos para facilitar o pedido de nota ou a localização de candidatos; também facilita a coleta de dados para ferramentas, como "Quem eu escolho?", que mostra as bandeiras de cada candidato (https://especiaisg1.globo/sp/sao-paulo/eleicoes/2020/quem-eu-escolho/sao-paulo);                
4) TSE deve oferecer cursos ou workshop online de R, SQL ou Python para estimular a produção de conteúdo com dados do repositório de dados. Conteúdo pode ser feito em parceria com ONGs, como a ABRAJI e a Escola de Dados, e as aulas devem ficar disponíveis na internet;                
5) Criação de painel para apresentar de forma consolidada números básicos de cada turno de eleição; por exemplo, número de prefeituras conquistadas por partido em cada UF (dados de eleições antigas disponíveis no repositório do TSE não estão completos);                
6) Informações das certidões criminais precisam estar em formato acessível, e não em PDF, permitindo que o cidadão saiba se o candidato é réu etc;                
7) TSE pode começar a oferecer arquivos em formato mais compactado, como GZ, e não apenas em CSV;                
8) DivulgaCand deve também mostrar o número total de votos de cada candidato;                
9) Outras bases de dados para o TSE discutir e se planejar para abrir no repositório de dados são: dados de mesário, transferência de título, eleitorado com biometria, locais remotos (com o número de eleitores em cada local e também com informações sobre o perfil do eleitorado);                
10) Após selecionar a base de dados de interesse, o internauta deve definir se deseja baixar os arquivos por UF ou do Brasil. Hoje, a pessoa precisa baixar tudo, o que torna o processo mais lento;                
11) Trabalho do Núcleo de Inteligência da Justiça Eleitoral (NIJE) deve ser mais bem divulgado e seus dados devem ser publicados (preferencialmente com o nome dos candidatos porque é de interesse público);                
12) Criação de uma base de dados de prefeitos e governadores que deixaram o cargo e dos vices que assumiram. Informar também caso algum presidente de Câmara Municipal/Assembleia Legislativa tenha tomado posse. Informar o motivo da renúncia, como candidatura a outro cargo eletivo, impeachment etc. Atualmente, sem essa informação, não há dado oficial para identificar vices que disputam a reeleição, e não a eleição;                
13) Criação de uma base de dados sobre multa aplicada a candidatos ou algo que mostre a fiscalização e a atuação dos TREs.               

Recomendações para bases de eleições antigas:                
14) TSE deve padronizar arquivos de eleições anteriores (principalmente a base de candidatos e de resultados), que não têm cabeçalho e que têm dificuldade em abrir considerando o separador. Também não há uma opção de arquivo BRASIL, o que facilitaria o acesso para boa parte dos usuários;                               
15) O cabeçalho de dados deve seguir os mesmos nomes do atual cabeçalho, mesmo que não inclua todas as colunas atualmente existentes;                
16) Base de candidatos de 2016 deve ter coluna com políticos eleitos, 2 turno etc;                
17) DivulgaCand de 2004 deve mostrar quais candidatos foram eleitos, suplentes etc;                
18) Coluna DS_DETALHE_SITUACAO_CAND deve sempre distinguir FALECIDO de qualquer outro termo e permitir o monitoramento de assassinatos de candidatos;                
19) Os dados de várias eleições antigas não estão completos. O estado do Rio de Janeiro, por exemplo, não tem arquivo para os anos de 1994 e 1996.               

Recomendações para a base CANDIDATOS:                
20) incluir link de site/página pessoal no Facebook/instagram do candidato no repositório (informação já presente do DivulgaCand);                
21) incluir link do PDF com a proposta de governo no repositório (informação já presente do DivulgaCand);                
22) coluna de reeleição deve ser conferida pelo TSE considerando eleições anteriores;                
23) coluna CPF deve ter validação com outra base pública (como a da Receita);                
24) coluna NM_TITULO_ELEITOR_CANDIDATO também deve ter validação;                
25) coluna NM_CANDIDATO deve ter validação com outra base pública (como a da Receita);                
26) TSE deve oferecer campo para candidato marcar se já concorreu em eleição anterior e poder importar campos já informados anteriormente;                
27) correção de nomes de municípios do Brasil, que variam de acordo com a grafia;                
28) criação de coluna que identifica se o município é capital ou não; 29) criação de coluna com o código do IBGE;                
30) criação de coluna para o candidato informar se tem alguma deficiência (deficiência física, auditiva, visual, intelectual, múltipla etc);                
31) criação de coluna para o candidato informar o bairro onde reside (para identificar quais são candidatos residentes no centro e na periferia, por exemplo);                
32) criação de coluna para o candidato informar se solicitou alguma licença para se candidatar por ser servidor público;                
33) coluna NM_SOCIAL_CANDIDATO não funciona bem, já que grande parte dos candidatos transgêneros já tem o nome social no RG e não precisa preenchê-la. Assim, a coluna NM_SOCIAL_CANDIDATO fica vazia mesmo quando o candidato é trans. O TSE deve estimular o preenchimento da coluna por candidatos trans.                
34) sequencial do candidato não pode mudar mesmo que ele atualize dados (é comum que se use a coluna para remover duplicatas);                
35) unificar o número sequencial do candidato, em diferentes eleições. Ou seja, facilitar a busca de um candidato em diferentes bases (e não só pelo CPF);                
36) efetiva padronização da coluna DS_SIT_TOT_TURNO, que tem valores como "NÃO ELEITO", "NAO ELEITO", "#NULO" e "#NULO#".               

Recomendações para a base BENS DE CANDIDATOS:                
37) candidato pode ter opção de inserir número de declaração de imposto de renda para a importação de dados da Receita Federal;                
38) coluna deve registrar se candidato optou por inserir informações direto da Receita ou se inseriu manualmente;                
39) campo de patrimônio deve alertar o candidato caso ele tenha inserido valor superior a R$ 1 milhão ou mesmo item com valor negativo (são inúmeros os erros de digitação);                
40) deixar mais claro para o candidato que patrimônio é até uma conta corrente com R$ 50, e não apenas posses a partir de R$ 300 mil reais, como no IRPF.                

Recomendações para a base PRESTAÇÃO DE CONTAS ELEITORAIS:                
41) coluna DS_CARGO usa os termos "Prefeito" e "Vereador", enquanto a base de candidato usa "PREFEITO" e "VEREADOR.                

Recomendações para a base RESULTADOS:                
42) Verificação se todos os municípios têm resultado para prefeito e vereador nas eleições ordinárias de cada ano. Dados antigos estão incompletos;                
43) Estabelecimento de data limite para a disponibilização dos dados completos e brutos no repositório de dados após a realização da eleição. Atualmente, os dados completos com o resultado demoram muitos dias para serem disponibilizados de forma efetivamente completa (o que atrapalha a cobertura eleitoral);                
44) Para candidatos sub judice, inserir situação (eleito ou não) ainda que o resultado aguarde julgamento.                

Recomendações para o dia da APURAÇÃO:                
45) Criar e disponibilizar painel com dados dos resultados eleitorais: por UF, por região, por partido, por tamanho da população etc;                
46) Facilitar o acesso aos dados de resultado eleitoral, em tempo real, a jornalistas, criando um sistema painel consolidado de dados, com opção de download dos dados brutos e também do recorte dos dados (sugestões serão coletados em consulta pública e curso com jornalistas);                
47) Um dos problemas é a falta de padronização de dados nacionais pela imprensa nas eleições municipais - quando não é possível detectar o motivo da divergência. Dados antigos mais importantes também devem ser informados consolidados em outra seção do site do TSE, como o Painel, para não haver risco de cada pessoa encontrar um número. Alguns desses dados são (por turno de eleição): número de prefeitos eleitos por cada partido no Brasil e em cada UF; número de vereadores eleitos por cada partido no Brasil e em cada UF; número de votos totais recebidos em cada disputa por partido; número de deputados estaduais/federais eleitos por partido no Brasil e em cada UF; e número de governadores eleitos por partido no Brasil e em cada UF. Outros recortes devem ser discutidos em consulta pública e a partir de demandas coletadas no curso com jornalistas;                
48) Disponibilização de latitude e longitude de cada seção eleitoral;                
49) Disponibilização de arquivo com o desenho de cada zona eleitoral.                

Recomendações para a base FILIADOS:               
50) Remoção de filiados que têm dados inválidos (datas inexistentes/observações duplicadas, inconsistência na situação da filiação etc);                
51) Padronização nas colunas de data de filiação, desfiliação e cancelamento. Recomendações para a base ELEITORADO:                
52) Documentar melhor onde está a base de locais de votação (hoje sob "Eleitorado > Eleitorado por local de votação", o que é super contraintuitivo)               

