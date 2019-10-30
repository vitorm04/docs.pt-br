---
title: Carregar dados de treinamento para o construtor de modelos
description: Saiba como carregar os dados de treinamento de um banco de SQL Server ou de um arquivo para uso em um dos cenários do construtor de modelos para ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 47dd32d18d00c33bcf51aa0ea3be8b22494ebc5f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041271"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="3aa0d-103">Carregar dados de treinamento no construtor de modelos</span><span class="sxs-lookup"><span data-stu-id="3aa0d-103">Load training data into Model Builder</span></span>

<span data-ttu-id="3aa0d-104">Saiba como carregar seus conjuntos de dados de treinamento de um arquivo ou de um SQL Server banco de dados para uso em um dos cenários do construtor de modelos para ML.NET.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="3aa0d-105">Os cenários do construtor de modelos podem usar SQL Server bancos de dados, arquivos de imagem e formatos de arquivo CSV ou TSV como dado de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="3aa0d-106">Limitações do conjunto de os conjuntos de modelos</span><span class="sxs-lookup"><span data-stu-id="3aa0d-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="3aa0d-107">O construtor de modelos limita a quantidade e o tipo de dados que você pode usar para modelos de treinamento:</span><span class="sxs-lookup"><span data-stu-id="3aa0d-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="3aa0d-108">Dados de SQL Server: 100.000 linhas</span><span class="sxs-lookup"><span data-stu-id="3aa0d-108">SQL Server data: 100,000 rows</span></span> 
- <span data-ttu-id="3aa0d-109">Arquivos CSV e TSV: sem limite de tamanho</span><span class="sxs-lookup"><span data-stu-id="3aa0d-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="3aa0d-110">Imagens: somente PNG e JPG.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="3aa0d-111">Cenários do construtor de modelos</span><span class="sxs-lookup"><span data-stu-id="3aa0d-111">Model Builder scenarios</span></span> 

<span data-ttu-id="3aa0d-112">O construtor de modelos ajuda a criar modelos para os seguintes cenários de aprendizado de máquina:</span><span class="sxs-lookup"><span data-stu-id="3aa0d-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="3aa0d-113">Análise de sentimentos (classificação binária): classificar dados textuais em duas categorias.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="3aa0d-114">Classificação do problema (classificação multiclasse): classificar dados textuais em três ou mais categorias.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="3aa0d-115">Previsão de preço (regressão): prever um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="3aa0d-116">Classificação de imagem (aprendizado profundo): categorizar imagens com base em características.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="3aa0d-117">Cenário personalizado: Crie cenários personalizados de seus dados usando regressão, classificação e outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="3aa0d-118">Este artigo aborda cenários de classificação e regressão com dados textuais ou numéricos e cenários de classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span> 

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="3aa0d-119">Carregar texto ou dados numéricos de um arquivo</span><span class="sxs-lookup"><span data-stu-id="3aa0d-119">Load text or numeric data from a file</span></span>  

<span data-ttu-id="3aa0d-120">Você pode carregar texto ou dados numéricos de um arquivo no construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="3aa0d-121">Ele aceita formatos de arquivo CSV (delimitados por vírgula) ou TSV (delimitados por tabulação).</span><span class="sxs-lookup"><span data-stu-id="3aa0d-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span> 

1. <span data-ttu-id="3aa0d-122">Na etapa dados do construtor de modelos, selecione **arquivo** na lista suspensa fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="3aa0d-123">Selecione o botão ao lado da caixa de texto **selecionar um arquivo** e use o explorador de arquivos para procurar e selecionar o arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="3aa0d-124">Escolha uma categoria na **coluna para prever (rótulo)** DropDown.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="3aa0d-125">Na lista suspensa **colunas de entrada (recursos)** , confirme se as colunas de dados que você deseja incluir estão marcadas.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="3aa0d-126">Você concluiu a configuração do arquivo de fonte de dados para o construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="3aa0d-127">Selecione o link **treinar** para mover para a próxima etapa no construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="3aa0d-128">Carregar dados de um banco de SQL Server</span><span class="sxs-lookup"><span data-stu-id="3aa0d-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="3aa0d-129">O construtor de modelos dá suporte ao carregamento de dados de bancos de dado de SQL Server locais e remotos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="3aa0d-130">Para carregar dados de um banco de dado SQL Server no construtor de módulos:</span><span class="sxs-lookup"><span data-stu-id="3aa0d-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="3aa0d-131">Na etapa dados do construtor de modelos, selecione **SQL Server** na lista suspensa fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="3aa0d-132">Selecione o botão ao lado da caixa de texto **conectar ao SQL Server banco de dados** .</span><span class="sxs-lookup"><span data-stu-id="3aa0d-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="3aa0d-133">Na caixa de diálogo **escolher dados** , selecione **Microsoft SQL Server arquivo de banco**.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span> 
    1. <span data-ttu-id="3aa0d-134">Desmarque a caixa de seleção **sempre usar esta seleção** e selecione **continuar**</span><span class="sxs-lookup"><span data-stu-id="3aa0d-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="3aa0d-135">Na caixa de diálogo **Propriedades da conexão** , selecione **procurar** e selecione o baixado. Arquivo MDF.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="3aa0d-136">Selecione **OK**</span><span class="sxs-lookup"><span data-stu-id="3aa0d-136">Select **OK**</span></span>
1. <span data-ttu-id="3aa0d-137">Escolha o nome do conjunto de campos na lista suspensa **nome da tabela** .</span><span class="sxs-lookup"><span data-stu-id="3aa0d-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="3aa0d-138">Na lista suspensa **coluna a prever (rótulo)** , escolha a categoria de dados na qual você deseja fazer uma previsão.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="3aa0d-139">Na lista suspensa **colunas de entrada (recursos)** , confirme se as colunas que você deseja incluir estão marcadas.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span> 

<span data-ttu-id="3aa0d-140">Você concluiu a configuração do arquivo de fonte de dados para o construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="3aa0d-141">Selecione o link **treinar** para mover para a próxima etapa no construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="3aa0d-142">Configurar arquivos de dados de imagem</span><span class="sxs-lookup"><span data-stu-id="3aa0d-142">Set up image data files</span></span>

<span data-ttu-id="3aa0d-143">O construtor de modelos espera que os dados de imagem sejam arquivos JPG ou PNG organizados em pastas que correspondam às categorias da classificação.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span> 

<span data-ttu-id="3aa0d-144">Para carregar imagens no construtor de modelos, forneça o caminho para um único diretório de nível superior:</span><span class="sxs-lookup"><span data-stu-id="3aa0d-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="3aa0d-145">Esse diretório de nível superior contém uma subpasta para cada uma das categorias a prever.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span> 
- <span data-ttu-id="3aa0d-146">Cada subpasta contém os arquivos de imagem pertencentes à sua categoria.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-146">Each subfolder contains the image files belonging to its category.</span></span> 
 
<span data-ttu-id="3aa0d-147">Na estrutura de pastas ilustrada abaixo, o diretório de nível superior é *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="3aa0d-148">Há cinco subdiretórios correspondentes às categorias que você deseja prever: Margarida, dandelion, rosas, flores e tulips.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="3aa0d-149">Cada um desses subdiretórios contém imagens que pertencem a sua respectiva categoria.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-149">Each of these subdirectories contains images belonging to its respective category.</span></span> 

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

## <a name="next-steps"></a><span data-ttu-id="3aa0d-150">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3aa0d-150">Next steps</span></span>
<span data-ttu-id="3aa0d-151">Siga estes tutoriais para criar aplicativos de Machine Learning com o construtor de modelos:</span><span class="sxs-lookup"><span data-stu-id="3aa0d-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="3aa0d-152">Prever os preços usando a regressão</span><span class="sxs-lookup"><span data-stu-id="3aa0d-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="3aa0d-153">Analisar sentimentos em um aplicativo Web usando a classificação binária</span><span class="sxs-lookup"><span data-stu-id="3aa0d-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="3aa0d-154">Se você estiver treinando um modelo usando código, [saiba como carregar dados usando a API ml.net](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="3aa0d-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
