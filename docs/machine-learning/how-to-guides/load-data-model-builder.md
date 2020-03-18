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
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="36b1b-103">Carregar dados de treinamento em Model Builder</span><span class="sxs-lookup"><span data-stu-id="36b1b-103">Load training data into Model Builder</span></span>

<span data-ttu-id="36b1b-104">Aprenda a carregar seus conjuntos de dados de treinamento a partir de um arquivo ou de um banco de dados Do SQL Server para uso em um dos cenários do Model Builder para ML.NET.</span><span class="sxs-lookup"><span data-stu-id="36b1b-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="36b1b-105">Os cenários do Model Builder podem usar bancos de dados sql server, arquivos de imagem e formatos de arquivos CSV ou TSV como dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="36b1b-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="36b1b-106">Limitações do conjunto de dados de treinamento no Model Builder</span><span class="sxs-lookup"><span data-stu-id="36b1b-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="36b1b-107">O Model Builder limita a quantidade e o tipo de dados que você pode usar para modelos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="36b1b-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="36b1b-108">Dados do SQL Server: 100.000 linhas</span><span class="sxs-lookup"><span data-stu-id="36b1b-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="36b1b-109">Arquivos CSV e TSV: Sem limite de tamanho</span><span class="sxs-lookup"><span data-stu-id="36b1b-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="36b1b-110">Imagens: SOMENTE PNG e JPG.</span><span class="sxs-lookup"><span data-stu-id="36b1b-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="36b1b-111">Cenários do Model Builder</span><span class="sxs-lookup"><span data-stu-id="36b1b-111">Model Builder scenarios</span></span>

<span data-ttu-id="36b1b-112">O Model Builder ajuda você a criar modelos para os seguintes cenários de aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="36b1b-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="36b1b-113">Análise de sentimento (classificação binária): Classificar dados texais em duas categorias.</span><span class="sxs-lookup"><span data-stu-id="36b1b-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="36b1b-114">Classificação de problemas (classificação multiclasse): Classificar dados texais em 3 ou mais categorias.</span><span class="sxs-lookup"><span data-stu-id="36b1b-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="36b1b-115">Previsão de preços (regressão): Prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="36b1b-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="36b1b-116">Classificação de imagem (deep learning): Categorizar imagens com base em características.</span><span class="sxs-lookup"><span data-stu-id="36b1b-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="36b1b-117">Cenário personalizado: Construa cenários personalizados a partir de seus dados usando regressão, classificação e outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="36b1b-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="36b1b-118">Este artigo abrange cenários de classificação e regressão com dados textuais ou numéricos e cenários de classificação de imagens.</span><span class="sxs-lookup"><span data-stu-id="36b1b-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="36b1b-119">Carregar texto ou dados numéricos de um arquivo</span><span class="sxs-lookup"><span data-stu-id="36b1b-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="36b1b-120">Você pode carregar texto ou dados numéricos de um arquivo no Model Builder.</span><span class="sxs-lookup"><span data-stu-id="36b1b-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="36b1b-121">Ele aceita formatos de arquivo comma-delimited (CSV) ou tab-delimited (TSV).</span><span class="sxs-lookup"><span data-stu-id="36b1b-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="36b1b-122">Na etapa de dados do Model Builder, selecione **Arquivo** a partir da gota de origem de dados.</span><span class="sxs-lookup"><span data-stu-id="36b1b-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="36b1b-123">Selecione o botão ao lado da **Caixa Selecionar uma** caixa de texto de arquivo e use o File Explorer para navegar e selecionar o arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="36b1b-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="36b1b-124">Escolha uma categoria na **estada Coluna para Prever (Rótulo).**</span><span class="sxs-lookup"><span data-stu-id="36b1b-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="36b1b-125">A partir da parada **Colunas de entrada (Recursos),** confirme se as colunas de dados que deseja incluir são verificadas.</span><span class="sxs-lookup"><span data-stu-id="36b1b-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="36b1b-126">Você terminou de configurar seu arquivo de origem de dados para Model Builder.</span><span class="sxs-lookup"><span data-stu-id="36b1b-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="36b1b-127">Selecione o link **Trem** para passar para a próxima etapa do Model Builder.</span><span class="sxs-lookup"><span data-stu-id="36b1b-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="36b1b-128">Carregar dados de um banco de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="36b1b-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="36b1b-129">O Model Builder suporta o carregamento de dados de bancos de dados SQL Server locais e remotos.</span><span class="sxs-lookup"><span data-stu-id="36b1b-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="36b1b-130">Para carregar dados de um banco de dados do SQL Server no Module Builder:</span><span class="sxs-lookup"><span data-stu-id="36b1b-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="36b1b-131">Na etapa de dados do Model Builder, selecione **SQL Server** a partir da gota de origem de dados.</span><span class="sxs-lookup"><span data-stu-id="36b1b-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="36b1b-132">Selecione o botão ao lado da caixa de texto **do banco de dados Connect to SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="36b1b-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="36b1b-133">Na caixa de diálogo **Escolher dados,** selecione **O arquivo de banco de dados do Microsoft SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="36b1b-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="36b1b-134">Desmarque o Use sempre esta caixa **de seleção** e selecione **Continuar**</span><span class="sxs-lookup"><span data-stu-id="36b1b-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="36b1b-135">Na caixa de diálogo Propriedades de **conexão,** **selecione Procurar** e selecione o baixado . Arquivo MDF.</span><span class="sxs-lookup"><span data-stu-id="36b1b-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="36b1b-136">Selecione **OK**</span><span class="sxs-lookup"><span data-stu-id="36b1b-136">Select **OK**</span></span>
1. <span data-ttu-id="36b1b-137">Escolha o nome do conjunto de dados na estada **nome da tabela.**</span><span class="sxs-lookup"><span data-stu-id="36b1b-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="36b1b-138">Na **parada Coluna para Prever (Rótulo),** escolha a categoria de dados na qual deseja fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="36b1b-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="36b1b-139">A partir da parada **Colunas de entrada (Recursos),** confirme se as colunas desejadas são verificadas.</span><span class="sxs-lookup"><span data-stu-id="36b1b-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="36b1b-140">Você terminou de configurar seu arquivo de origem de dados para Model Builder.</span><span class="sxs-lookup"><span data-stu-id="36b1b-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="36b1b-141">Selecione o link **Trem** para passar para a próxima etapa do Model Builder.</span><span class="sxs-lookup"><span data-stu-id="36b1b-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="36b1b-142">Configurar arquivos de dados de imagem</span><span class="sxs-lookup"><span data-stu-id="36b1b-142">Set up image data files</span></span>

<span data-ttu-id="36b1b-143">O Model Builder espera que os dados de imagem sejam arquivos JPG ou PNG organizados em pastas que correspondam às categorias da classificação.</span><span class="sxs-lookup"><span data-stu-id="36b1b-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="36b1b-144">Para carregar imagens no Model Builder, forneça o caminho para um único diretório de nível superior:</span><span class="sxs-lookup"><span data-stu-id="36b1b-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="36b1b-145">Este diretório de alto nível contém uma subpasta para cada uma das categorias a prever.</span><span class="sxs-lookup"><span data-stu-id="36b1b-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="36b1b-146">Cada subpasta contém os arquivos de imagem pertencentes à sua categoria.</span><span class="sxs-lookup"><span data-stu-id="36b1b-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="36b1b-147">Na estrutura da pasta ilustrada abaixo, o diretório de alto nível é *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="36b1b-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="36b1b-148">Existem cinco subdiretórios correspondentes às categorias que você deseja prever: margarida, dente-de-leão, rosas, girassóis e tulipas.</span><span class="sxs-lookup"><span data-stu-id="36b1b-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="36b1b-149">Cada um desses subdiretórios contém imagens pertencentes à sua respectiva categoria.</span><span class="sxs-lookup"><span data-stu-id="36b1b-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="36b1b-150">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="36b1b-150">Next steps</span></span>

<span data-ttu-id="36b1b-151">Siga estes tutoriais para criar aplicativos de aprendizado de máquina com o Model Builder:</span><span class="sxs-lookup"><span data-stu-id="36b1b-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="36b1b-152">Prever os preços usando regressão</span><span class="sxs-lookup"><span data-stu-id="36b1b-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="36b1b-153">Analisar o sentimento em uma aplicação web usando classificação binária</span><span class="sxs-lookup"><span data-stu-id="36b1b-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="36b1b-154">Se você está treinando um modelo usando código, [aprenda a carregar dados usando a API ML.NET](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="36b1b-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
