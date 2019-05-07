---
title: "Funções básicas do R para jornalistas - 2"
author: "Gabriela Caesar"
date: "2019-05-07"
output: html_document
---

## Tutorial 2

![](https://cdn-images-1.medium.com/max/1200/1*xvzhZtBfl3hqnF0AMdoIUA.gif)

Este caderno mostra as funções básicas da linguagem de programação R que podem ser úteis para jornalistas. Anteriormente, eu fiz tutoriais com o [básico do Google Spreadsheet para jornalista](https://medium.com/@gabrielacaesar/o-b%C3%A1sico-de-google-spreadsheet-para-jornalistas-fun%C3%A7%C3%B5es-matem%C3%A1ticas-e3b87e5371d6).

Caso você não tenha o RStudio na sua máquina, por favor siga o passo a passo deste tutorial (em inglês) para [Mac](https://medium.com/@GalarnykMichael/install-r-and-rstudio-on-mac-e911606ce4f4) e [Windows](https://medium.com/@GalarnykMichael/install-r-and-rstudio-on-windows-5f503f708027). Também recomendo que você baixe um editor de texto, como o [Sublime](https://www.sublimetext.com/3).

Cada bloco de código, também chamado de “chunk”, tem uma função diferente. Para criar um arquivo `"R Markdown"`, assim como este caderno, abra o RStudio, clique em `"File" > "New File" > "R Markdown"`. Ou, se não for escrever muito, crie um `"R Script"`.

Para rodar o código, selecione o trecho e clique em `command + enter` no Mac (ou `CTRL + enter` no Windows). No `"R Markdown"`, também é possível clicar na seta verde à direita.

São, no total, três cadernos de R para jornalistas:

* [Instalação, leitura e verificação](https://www.gabrielacaesar.com/2019/05/02/fun%C3%A7%C3%B5es-b%C3%A1sicas-do-r-para-jornalistas-1/);   
* Limpeza, renomeações e modificações (este post);    
* Análise de dados e criação de gráficos (em breve).   

## Carregar bibliotecas
Desta vez, nós não precisamos instalar as bibliotecas, com `install.packages()` porque já fizemos esse procedimento na primeira etapa do tutorial. Agora, apenas vamos "chamar" as bibliotecas.

```{r message=FALSE}
# install.packages("data.table")
# install.packages("tidyverse")
# install.packages("ggplot2")

library(data.table)
library(tidyverse)
library(ggplot2)
```

## Importar e ver as colunas
Como estamos trabalhando noutro caderno - e o arquivo ainda não foi "chamado" aqui -, nós também precisamos repetir esse procedimento, com `fread()`. Vamos escolher o nome "cota_senado" para chamar o nosso arquivo que está hospedado no link mencionado no bloco de código abaixo.

Para saber quais são as colunas do nosso arquivo, usamos depois a função `colnames()`.

```{r}
cota_senado <- fread("https://gist.githubusercontent.com/gcaesar27/5faede8c1c6ffc82c7145dc3ececcbfe/raw/f3192ff17214c3c5d8eca4ebad42ba6f70d409aa/cota-senado-30-abril-2019", encoding = "UTF-8")

colnames(cota_senado)
```

## Deletar coluna
Nós queremos deletar uma das colunas do nosso arquivo. Por isso, vamos rodar o código abaixo. Logo depois, nós vamos rodar o `colnames(cota_senado)` para confirmar que a coluna foi removida.

```{r}
cota_senado$DOCUMENTO <- NULL

colnames(cota_senado)
```

## Criar coluna
Da mesma forma, nós também podemos criar uma coluna. Como estamos na parte introdutória do R, todos os valores da nova coluna serão iguais. A nova coluna se chama "CASA" e recebe o valor "SENADO FEDERAL".

Também vamos rodar `colnames(cota_senado)` para confirmar que a nova coluna foi criada.
```{r}
cota_senado$CASA <- "SENADO FEDERAL"

colnames(cota_senado)
```

## Contar linhas
A função `nrow()` nos informa o número de linhas.
```{r}
nrow(cota_senado)
```

## Substituir vírgula por ponto
O nosso arquivo usa o padrão brasileiro de separar os reais dos centavos com vírgulas. Queremos substituir a vírgula por ponto. Essa mudança deve ocorrer apenas na coluna "VALOR_REEMBOLSO".

```{r}
cota_senado$VALOR_REEMBOLSADO <- gsub("\\,", ".", cota_senado$VALOR_REEMBOLSADO)

head(cota_senado$VALOR_REEMBOLSADO)
```

## Mudar a classe
Quando importamos o arquivo, a gente não informou as classes de cada coluna. Identificamos na primeira etapa do tutorial, porém, que a coluna "VALOR_REEMBOLSADO" foi registrada como "character" (ou seja, texto). Agora queremos convertê-la para número.

Por isso, usaremos a função `as.numeric()` e depois verificamos a classe da coluna com `typeof()`.

```{r}
cota_senado$VALOR_REEMBOLSADO <- as.numeric(cota_senado$VALOR_REEMBOLSADO)

typeof(cota_senado$VALOR_REEMBOLSADO)
```

## Somar valores
Abaixo, nós usamos a função `sum()` para somar todos os valores da coluna "VALOR_REEMBOLSO". Assim, descobrimos qual foi o total, em reais, de reembolsos a senadores.

```{r}
sum(cota_senado$VALOR_REEMBOLSADO)

```

## Colocar em caixa baixa
A função `tolower()` coloca todo o texto em caixa baixa. Para mostrar como funciona, vamos aplicar essa função à coluna "SENADOR", que no arquivo importado tem os valores em caixa alta.

Podemos criar uma nova coluna com os valores em caixa baixa ou sobrescrever aquela coluna. Aqui, optamos por criar uma nova coluna. Usamos a função `head(cota_senado, 3)` em seguida para verificar o arquivo.
```{r}
cota_senado$senador_lower <- tolower(cota_senado$SENADOR)

head(cota_senado, 3)
```

## Colocar em caixa alta
Vemos que a coluna "FORNECEDOR" tem valores que são em caixa alta e baixa, outros apenas em caixa alta e várias despadronizações. Por isso, vamos usar a função `toupper()` para colocar todo o texto em caixa alta. 

Vamos sobrescrever a coluna "FORNECEDOR" e colocar tudo em caixa alta. Usamos a função `head(cota_senado, 3)` em seguida para verificar o arquivo.
```{r}
cota_senado$FORNECEDOR <- toupper(cota_senado$FORNECEDOR)

head(cota_senado, 3)
```

## Tirar a acentuação
Também para ajudar na padronização, nós ainda vamos tirar a acentuação de todos os valores da coluna "FORNECEDOR". 

Perceba, porém, que a coluna "CNPJ_CPF" pode ser mais valiosa para a análise, considerando que é mais fácil que várias pessoas tenham digitado os números de forma padronizada do que os nomes.

```{r}
fornecedor_sem_acentuacao <- as.data.frame(iconv(cota_senado$FORNECEDOR, from = "UTF-8", to = "ASCII//TRANSLIT"))

head(fornecedor_sem_acentuacao)
```

## Juntar dois (ou mais) arquivos
Queremos juntar a coluna criada acima, que contém os nomes dos fornecedores sem acento e em caixa alta, ao arquivo inicial, chamado "cota_senado". Por isso, vamos usar a função `cbind()`. 

Na prática, a gente pegou o arquivo "cota_senado" e acrescentou a coluna criada acima. O nosso novo arquivo recebe o nome "cota_senado_final".

```{r}
cota_senado_final <- cbind(fornecedor_sem_acentuacao, cota_senado)

head(cota_senado_final)
```

## Empilhar dois (ou mais) arquivos

O TSE, por exemplo, costuma divulgar vários arquivos, sendo que cada um se refere a uma UF. Para juntar todos esses arquivos em apenas um único arquivo, a função `bind_rows()` é a indicada.

Da mesma forma, se o Senado Federal divulga um arquivo por ano - e todas as colunas são iguais -, a gente pode usar a função `bind_rows()` para empilhar os arquivos de cada ano. Para rodar essa função, nós vamos precisa instalar (caso ainda não tenha instalado) e carregar a biblioteca `dplyr`.

No fim, usamos a função `unique()` apenas para confirmar que todos os arquivos foram empilhados em "cota_senado_2017_a_2019" - ou seja, que os anos 2017, 2018 e 2019 aparecem na coluna "ANO".

```{r message=FALSE}
# install.packages("dplyr")
library(dplyr)
```

```{r}
cota_senado_2019 <- fread("https://gist.githubusercontent.com/gcaesar27/dc9917f96f9acf993f38cb9f1758c96e/raw/e841264cc65b160c0b9b68009ed030e49c32b384/cota-senado-2019-07-maio-2019", encoding = "UTF-8")
cota_senado_2018 <- fread("https://gist.githubusercontent.com/gcaesar27/c4719807b306af9166f53ccab54cb9fd/raw/e0e5a2fedc585dc1b19797b47921652446b76ebf/cota-senado-2018-7-maio-2019", encoding = "UTF-8")
cota_senado_2017 <- fread("https://gist.githubusercontent.com/gcaesar27/d407feb3da6d275ee7aa6b226ff03172/raw/99255221a8e4a2759609be67ed54c55f6189fd0b/cota-senado-2017-07-maio-2019", encoding = "UTF-8")
  
cota_senado_2017_a_2019 <- bind_rows(cota_senado_2019, cota_senado_2018, cota_senado_2017)

unique(cota_senado_2017_a_2019$ANO)

```

## Separar em duas (ou mais) colunas
A coluna "DATA" tem o seguinte formato: dia/mês/ano. Queremos criar uma coluna apenas com o valor do dia. Outra que tenha apenas o valor do mês. E a terceira com o valor do ano. O separador, no caso, é "/". 

Como queremos manter a atual coluna "DATA", a gente também informar que "remove = FALSE" (por padrão, o remove = TRUE). Para tudo isso, usamos a função `separate()`. Essa função é da biblioteca `tidyr`, que precisa ser instalada e carregada.

```{r message=FALSE}
# install.packages("tidyr")
library(tidyr)
```

```{r}
cota_senado_final <- separate(cota_senado_final, DATA, c("DIA", "MES", "ANO"), sep = "/", remove = FALSE)

head(cota_senado_final)
```

## Unir em uma única coluna
Caso quiséssemos fazer o procedimento contrário - juntar várias colunas em apenas uma única -, a gente usaria a função `unite`. A gente informou o nome da nova coluna, "DATA_NEW", depois os nomes das colunas que vão se juntar e também o separador dos valores ("-"). 

Desta vez, optamos por não informar se queremos ou não manter as colunas "DIA", "MES" e "ANO", então o que vale é o padrão. Por padrão, o "remove = TRUE". Isso é sempre claro na documentação do R, que pode ser acessada ao digitar no console `?unite` ou ao pesquisar no site [www.rdocumentation.org](www.rdocumentation.org).

```{r}
cota_senado_final <- unite(cota_senado_final, "DATA_NEW", c("DIA", "MES", "ANO"), sep = "-")

head(cota_senado_final)
```
