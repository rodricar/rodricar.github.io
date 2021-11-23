Endangered Species in Brazil
========================================================
author: Rejane Rodrigues de Carvalho Pereira
date: November 22, 2021
autosize: true


Step 1 - Downloading and Reading the File (Code)
========================================================


```r
library(tidyverse)


# DOWNLOADING THE FILE.

fileUrl <- "http://dados.mma.gov.br/dataset/41a79b71-445f-4a6a-8c70-d46af991292a/resource/1f13b062-f3f6-4198-a4c5-3581548bebec/download/lista-de-especies-ameacas-2020.csv"

setwd("C:/Users/Rejane/Documents/Cursos_R/Developing_Data_Products/")

download.file(fileUrl, 
              destfile = "lista-de-especies-ameacas-2020.csv", 
              method = "auto")

# READING THE FILE.
endangered_species <- data.table::fread("lista-de-especies-ameacas-2020.csv",                                           encoding = "UTF-8") %>%
janitor::clean_names()
```

Step 3 - Reading the File (Structure File)
========================================================


```r
dplyr::glimpse(endangered_species)
```

```
Rows: 3,287
Columns: 15
$ fauna_flora                                 <chr> "Flora", "Fauna", "Flora",~
$ grupo                                       <chr> "Angiospermas", "Aves", "A~
$ familia                                     <chr> "Salicaceae", "Cracidae", ~
$ especie_simplificado                        <chr> "Abatia angeliana", "Aburr~
$ nome_comum                                  <chr> "-", "Jacutinga", "-", "-"~
$ categoria_de_ameaca                         <chr> "Vulnerável (VU)", "Em Per~
$ sigla_categoria_de_ameaca                   <chr> "VU", "EN", "CR", "CR", "V~
$ bioma                                       <chr> "Mata Atlântica", "Cerrado~
$ principais_ameacas                          <chr> "Perda de Habitat/Degradaç~
$ presenca_em_areas_protegidas                <chr> "Sim", "Sim", "Sim", "Sim"~
$ plano_de_acao_nacional_para_conservacao_pan <chr> "Sim", "Não", "Sim", "Não"~
$ ordenamento_pesqueiro                       <chr> "Não", "Não", "Não", "Não"~
$ nivel_de_protecao_na_estrategia_nacional    <int> 2, 4, 2, 2, 2, 3, 2, 2, 3,~
$ especie_exclusiva_do_brasil                 <chr> "Sim", "Não", "Sim", "Sim"~
$ estados_de_ocorrencia                       <chr> "PR", "BA; ES; MG; PR; RJ;~
```

Step 4 - Birds Endangered exclusive from Brazil
========================================================


```r
# SELECTING ONLY THE BRASILIAN FAUNA's BIRDS.
fauna <- endangered_species %>%
         filter(fauna_flora %in% "Fauna" &
                grupo %in% "Aves" &
                especie_exclusiva_do_brasil %in% "Sim") %>%
         select(-fauna_flora, -grupo, -especie_exclusiva_do_brasil)

dplyr::glimpse(fauna)
```

```
Rows: 162
Columns: 12
$ familia                                     <chr> "Furnariidae", "Accipitrid~
$ especie_simplificado                        <chr> "Acrobatornis fonsecai", "~
$ nome_comum                                  <chr> "Acrobata", "Gavião-pombo-~
$ categoria_de_ameaca                         <chr> "Vulnerável (VU)", "Vulner~
$ sigla_categoria_de_ameaca                   <chr> "VU", "VU", "VU", "EN", "C~
$ bioma                                       <chr> "Mata Atlântica", "Caating~
$ principais_ameacas                          <chr> "Agropecuária", "Agropecuá~
$ presenca_em_areas_protegidas                <chr> "Sim", "Sim", "Sim", "Sim"~
$ plano_de_acao_nacional_para_conservacao_pan <chr> "Não", "Não", "Não", "Não"~
$ ordenamento_pesqueiro                       <chr> "Não", "Não", "Não", "Não"~
$ nivel_de_protecao_na_estrategia_nacional    <int> 2, 4, 4, 3, 2, 3, 3, 2, 3,~
$ estados_de_ocorrencia                       <chr> "BA; MG", "BA; ES; MG; PR;~
```

PLOT: Fauna' Birds Endangered in Brazil



```
Error in path.expand(path) : invalid 'path' argument
```
