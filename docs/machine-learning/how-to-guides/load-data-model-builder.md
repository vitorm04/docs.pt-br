---
title: Carregar dados de treinamento para Model Builder
description: Aprenda a carregar dados de treinamento de um banco de dados do SQL Server ou de um arquivo para uso em um dos cenários do Model Builder para ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849153"
---
# <a name="load-training-data-into-model-builder"></a>Carregar dados de treinamento em Model Builder

Aprenda a carregar seus conjuntos de dados de treinamento a partir de um arquivo ou de um banco de dados Do SQL Server para uso em um dos cenários do Model Builder para ML.NET. Os cenários do Model Builder podem usar bancos de dados sql server, arquivos de imagem e formatos de arquivos CSV ou TSV como dados de treinamento.

## <a name="training-dataset-limitations-in-model-builder"></a>Limitações do conjunto de dados de treinamento no Model Builder

O Model Builder limita a quantidade e o tipo de dados que você pode usar para modelos de treinamento:

- Dados do SQL Server: 100.000 linhas
- Arquivos CSV e TSV: Sem limite de tamanho
- Imagens: SOMENTE PNG e JPG.

## <a name="model-builder-scenarios"></a>Cenários do Model Builder

O Model Builder ajuda você a criar modelos para os seguintes cenários de aprendizado de máquina:

- Análise de sentimento (classificação binária): Classificar dados texais em duas categorias.
- Classificação de problemas (classificação multiclasse): Classificar dados texais em 3 ou mais categorias.
- Previsão de preços (regressão): Prever um valor numérico.
- Classificação de imagem (deep learning): Categorizar imagens com base em características.
- Cenário personalizado: Construa cenários personalizados a partir de seus dados usando regressão, classificação e outras tarefas.

Este artigo abrange cenários de classificação e regressão com dados textuais ou numéricos e cenários de classificação de imagens.

## <a name="load-text-or-numeric-data-from-a-file"></a>Carregar texto ou dados numéricos de um arquivo

Você pode carregar texto ou dados numéricos de um arquivo no Model Builder. Ele aceita formatos de arquivo comma-delimited (CSV) ou tab-delimited (TSV).

1. Na etapa de dados do Model Builder, selecione **Arquivo** a partir da gota de origem de dados.
2. Selecione o botão ao lado da **Caixa Selecionar uma** caixa de texto de arquivo e use o File Explorer para navegar e selecionar o arquivo de dados.
3. Escolha uma categoria na **estada Coluna para Prever (Rótulo).**
4. A partir da parada **Colunas de entrada (Recursos),** confirme se as colunas de dados que deseja incluir são verificadas.

Você terminou de configurar seu arquivo de origem de dados para Model Builder. Selecione o link **Trem** para passar para a próxima etapa do Model Builder.

## <a name="load-data-from-a-sql-server-database"></a>Carregar dados de um banco de dados do SQL Server

O Model Builder suporta o carregamento de dados de bancos de dados SQL Server locais e remotos.

Para carregar dados de um banco de dados do SQL Server no Module Builder:

1. Na etapa de dados do Model Builder, selecione **SQL Server** a partir da gota de origem de dados.
1. Selecione o botão ao lado da caixa de texto **do banco de dados Connect to SQL Server.**
    1. Na caixa de diálogo **Escolher dados,** selecione **O arquivo de banco de dados do Microsoft SQL Server**.
    1. Desmarque o Use sempre esta caixa **de seleção** e selecione **Continuar**
    1. Na caixa de diálogo Propriedades de **conexão,** **selecione Procurar** e selecione o baixado . Arquivo MDF.
    1. Selecione **OK**
1. Escolha o nome do conjunto de dados na estada **nome da tabela.**
1. Na **parada Coluna para Prever (Rótulo),** escolha a categoria de dados na qual deseja fazer uma previsão.
1. A partir da parada **Colunas de entrada (Recursos),** confirme se as colunas desejadas são verificadas.

Você terminou de configurar seu arquivo de origem de dados para Model Builder. Selecione o link **Trem** para passar para a próxima etapa do Model Builder.

## <a name="set-up-image-data-files"></a>Configurar arquivos de dados de imagem

O Model Builder espera que os dados de imagem sejam arquivos JPG ou PNG organizados em pastas que correspondam às categorias da classificação.

Para carregar imagens no Model Builder, forneça o caminho para um único diretório de nível superior:

- Este diretório de alto nível contém uma subpasta para cada uma das categorias a prever.
- Cada subpasta contém os arquivos de imagem pertencentes à sua categoria.

Na estrutura da pasta ilustrada abaixo, o diretório de alto nível é *flower_photos*. Existem cinco subdiretórios correspondentes às categorias que você deseja prever: margarida, dente-de-leão, rosas, girassóis e tulipas. Cada um desses subdiretórios contém imagens pertencentes à sua respectiva categoria.

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a>Próximas etapas

Siga estes tutoriais para criar aplicativos de aprendizado de máquina com o Model Builder:

- [Prever os preços usando regressão](../tutorials/predict-prices-with-model-builder.md)
- [Analisar o sentimento em uma aplicação web usando classificação binária](../tutorials/sentiment-analysis-model-builder.md )

Se você está treinando um modelo usando código, [aprenda a carregar dados usando a API ML.NET](load-data-ml-net.md).
