---
title: 'Tutorial: Inspeção visual automatizada usando aprendizado de transferência'
description: Este tutorial ilustra como usar o aprendizado de transferência para treinar um modelo de aprendizagem profunda TensorFlow em ML.NET usando a API de detecção de imagem para classificar imagens de superfícies de concreto como rachadas ou não rachadas.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920095"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="a52c6-103">Tutorial: Inspeção visual automatizada usando aprendizado de transferência com a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="a52c6-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="a52c6-104">Aprenda a treinar um modelo de aprendizagem profunda personalizado usando o aprendizado de transferência, um modelo TensorFlow pré-treinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies de concreto como rachadas ou não rachadas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="a52c6-105">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="a52c6-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a52c6-106">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="a52c6-106">Understand the problem</span></span>
> - <span data-ttu-id="a52c6-107">Conheça a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="a52c6-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="a52c6-108">Entenda o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="a52c6-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="a52c6-109">Use o aprendizado de transferência para treinar um modelo personalizado de classificação de imagem TensorFlow</span><span class="sxs-lookup"><span data-stu-id="a52c6-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="a52c6-110">Classificar imagens com o modelo personalizado</span><span class="sxs-lookup"><span data-stu-id="a52c6-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a52c6-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a52c6-111">Prerequisites</span></span>

- <span data-ttu-id="a52c6-112">[Visual Studio 2017 versão 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho ".NET Core cross-platform development" instalada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-112">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="a52c6-113">Visão geral da amostra de aprendizado de transferência de classificação de imagem</span><span class="sxs-lookup"><span data-stu-id="a52c6-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="a52c6-114">Esta amostra é um aplicativo de console C# .NET Core que classifica as imagens usando um modelo tensorFlow de aprendizado profundo pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="a52c6-115">O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="a52c6-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="a52c6-116">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="a52c6-116">Understand the problem</span></span>

<span data-ttu-id="a52c6-117">A classificação de imagem é um problema de visão computacional.</span><span class="sxs-lookup"><span data-stu-id="a52c6-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="a52c6-118">A classificação da imagem toma uma imagem como entrada e a categoriza em uma classe prescrita.</span><span class="sxs-lookup"><span data-stu-id="a52c6-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="a52c6-119">Alguns cenários em que a classificação de imagem é útil incluem:</span><span class="sxs-lookup"><span data-stu-id="a52c6-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="a52c6-120">Reconhecimento de rosto</span><span class="sxs-lookup"><span data-stu-id="a52c6-120">Facial recognition</span></span>
- <span data-ttu-id="a52c6-121">Detecção de emoções</span><span class="sxs-lookup"><span data-stu-id="a52c6-121">Emotion detection</span></span>
- <span data-ttu-id="a52c6-122">Diagnóstico médico</span><span class="sxs-lookup"><span data-stu-id="a52c6-122">Medical diagnosis</span></span>
- <span data-ttu-id="a52c6-123">Detecção de monumentos</span><span class="sxs-lookup"><span data-stu-id="a52c6-123">Landmark detection</span></span>

<span data-ttu-id="a52c6-124">Este tutorial treina um modelo personalizado de classificação de imagens para realizar inspeção visual automatizada de decks de ponte para identificar estruturas que são danificadas por rachaduras.</span><span class="sxs-lookup"><span data-stu-id="a52c6-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="a52c6-125">API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="a52c6-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="a52c6-126">ML.NET fornece várias maneiras de realizar a classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="a52c6-127">Este tutorial aplica o aprendizado de transferência usando a API de classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="a52c6-128">A API de classificação de imagem faz uso de [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), uma biblioteca de baixo nível que fornece vinculações C# para a API TensorFlow C++.</span><span class="sxs-lookup"><span data-stu-id="a52c6-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="a52c6-129">O que é o aprendizado por transferência?</span><span class="sxs-lookup"><span data-stu-id="a52c6-129">What is transfer learning?</span></span>

<span data-ttu-id="a52c6-130">Transferir aprendizagem aplica conhecimento adquirido ao resolver um problema para outro problema relacionado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="a52c6-131">Treinar um modelo de aprendizagem profunda do zero requer a definição de vários parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos computacionais (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="a52c6-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="a52c6-132">O uso de um modelo pré-treinado, juntamente com o aprendizado de transferência, permite que você insere o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="a52c6-133">Processo de treinamento</span><span class="sxs-lookup"><span data-stu-id="a52c6-133">Training process</span></span>

<span data-ttu-id="a52c6-134">A API de classificação de imagem inicia o processo de treinamento carregando um modelo TensorFlow pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="a52c6-135">O processo de treinamento consiste em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="a52c6-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="a52c6-136">Fase de gargalo</span><span class="sxs-lookup"><span data-stu-id="a52c6-136">Bottleneck phase</span></span>
2. <span data-ttu-id="a52c6-137">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="a52c6-137">Training phase</span></span>

![Etapas de treinamento](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="a52c6-139">Fase de gargalo</span><span class="sxs-lookup"><span data-stu-id="a52c6-139">Bottleneck phase</span></span>

<span data-ttu-id="a52c6-140">Durante a fase de gargalo, o conjunto de imagens de treinamento é carregado e os valores de pixel são usados como entrada, ou recursos, para as camadas congeladas do modelo pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="a52c6-141">As camadas congeladas incluem todas as camadas da rede neural até a penúltima camada, informalmente conhecida como a camada de gargalo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="a52c6-142">Essas camadas são referidas como congeladas porque nenhum treinamento ocorrerá nessas camadas e as operações são de passagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="a52c6-143">É nessas camadas congeladas onde os padrões de nível inferior que ajudam um modelo a diferenciar entre as diferentes classes são computados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="a52c6-144">Quanto maior o número de camadas, mais intensivo computacionalmente esta etapa é.</span><span class="sxs-lookup"><span data-stu-id="a52c6-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="a52c6-145">Felizmente, como este é um cálculo único, os resultados podem ser armazenados em cache e usados em corridas posteriores ao experimentar com diferentes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a52c6-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="a52c6-146">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="a52c6-146">Training phase</span></span>

<span data-ttu-id="a52c6-147">Uma vez que os valores de saída da fase de gargalo são calculados, eles são usados como entrada para retreinar a camada final do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="a52c6-148">Este processo é iterativo e executa para o número de vezes especificado por parâmetros do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="a52c6-149">Durante cada corrida, a perda e a precisão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="a52c6-150">Em seguida, os ajustes apropriados são feitos para melhorar o modelo com o objetivo de minimizar a perda e maximizar a precisão.</span><span class="sxs-lookup"><span data-stu-id="a52c6-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="a52c6-151">Uma vez que o treinamento é concluído, dois formatos de modelo são de saída.</span><span class="sxs-lookup"><span data-stu-id="a52c6-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="a52c6-152">Uma delas é `.pb` a versão do modelo `.zip` e a outra é a ML.NET versão serializada do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="a52c6-153">Ao trabalhar em ambientes suportados por ML.NET, `.zip` recomenda-se usar a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="a52c6-154">No entanto, em ambientes onde ML.NET não é `.pb` suportado, você tem a opção de usar a versão.</span><span class="sxs-lookup"><span data-stu-id="a52c6-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="a52c6-155">Entenda o modelo pré-treinado</span><span class="sxs-lookup"><span data-stu-id="a52c6-155">Understand the pretrained model</span></span>

<span data-ttu-id="a52c6-156">O modelo pré-treinado usado neste tutorial é a variante de 101 camadas do modelo V2 da Rede Residual (ResNet).</span><span class="sxs-lookup"><span data-stu-id="a52c6-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="a52c6-157">O modelo original é treinado para classificar imagens em mil categorias.</span><span class="sxs-lookup"><span data-stu-id="a52c6-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="a52c6-158">O modelo toma como entrada uma imagem de tamanho 224 x 224 e produz as probabilidades de classe para cada uma das classes em que é treinado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="a52c6-159">Parte deste modelo é usado para treinar um novo modelo usando imagens personalizadas para fazer previsões entre duas classes.</span><span class="sxs-lookup"><span data-stu-id="a52c6-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="a52c6-160">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="a52c6-160">Create console application</span></span>

<span data-ttu-id="a52c6-161">Agora que você tem uma compreensão geral do aprendizado de transferência e da API de classificação de imagem, é hora de construir o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="a52c6-162">Crie um **aplicativo de console C# .NET Core** chamado "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="a52c6-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="a52c6-163">Instale o pacote **1.4.0** NuGet versão **Microsoft.ML:**</span><span class="sxs-lookup"><span data-stu-id="a52c6-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="a52c6-164">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a52c6-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="a52c6-165">Escolha "nuget.org" como fonte do Pacote.</span><span class="sxs-lookup"><span data-stu-id="a52c6-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="a52c6-166">Selecione a guia **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="a52c6-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="a52c6-167">Verifique a **caixa de seleção Incluir pré-lançamento.**</span><span class="sxs-lookup"><span data-stu-id="a52c6-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="a52c6-168">Procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="a52c6-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="a52c6-169">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="a52c6-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="a52c6-170">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="a52c6-171">Repita essas etapas para os pacotes **Microsoft.ML.Vision** **1.4.0**, **SciSharp.TensorFlow.Redist** **versão 1.15.0**e **Microsoft.ML.ImageAnalytics** versão **1.4.0** NuGet.</span><span class="sxs-lookup"><span data-stu-id="a52c6-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a52c6-172">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="a52c6-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="a52c6-173">Os conjuntos de dados para este tutorial são de Maguire, Marc; Dorafshan, Sattar; e Thomas, Robert J., "SDNET2018: Um conjunto de dados de imagem de crack concreto para aplicações de aprendizagem de máquina" (2018).</span><span class="sxs-lookup"><span data-stu-id="a52c6-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="a52c6-174">Navegue por todos os conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-174">Browse all Datasets.</span></span> <span data-ttu-id="a52c6-175">Papel 48.</span><span class="sxs-lookup"><span data-stu-id="a52c6-175">Paper 48.</span></span> <span data-ttu-id="a52c6-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="a52c6-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="a52c6-177">SDNET2018 é um conjunto de dados de imagem que contém anotações para estruturas de concreto rachadas e não rachadas (decks de ponte, paredes e pavimento).</span><span class="sxs-lookup"><span data-stu-id="a52c6-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Amostras do deck da ponte do conjunto de dados SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="a52c6-179">Os dados estão organizados em três subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="a52c6-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="a52c6-180">D contém imagens do convés da ponte</span><span class="sxs-lookup"><span data-stu-id="a52c6-180">D contains bridge deck images</span></span>
- <span data-ttu-id="a52c6-181">P contém imagens de pavimento</span><span class="sxs-lookup"><span data-stu-id="a52c6-181">P contains pavement images</span></span>
- <span data-ttu-id="a52c6-182">W contém imagens de parede</span><span class="sxs-lookup"><span data-stu-id="a52c6-182">W contains wall images</span></span>

<span data-ttu-id="a52c6-183">Cada um desses subdiretórios contém dois subdiretórios prefixados adicionais:</span><span class="sxs-lookup"><span data-stu-id="a52c6-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="a52c6-184">C é o prefixo usado para superfícies rachadas</span><span class="sxs-lookup"><span data-stu-id="a52c6-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="a52c6-185">U é o prefixo usado para superfícies não rachadas</span><span class="sxs-lookup"><span data-stu-id="a52c6-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="a52c6-186">Neste tutorial, apenas imagens de deck de ponte são usadas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="a52c6-187">Baixe o [conjunto de dados](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) e desfaça o zíper.</span><span class="sxs-lookup"><span data-stu-id="a52c6-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="a52c6-188">Crie um diretório chamado "assets" em seu projeto para salvar seus arquivos de conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="a52c6-189">Copie os subdiretórios *de CD* e *UD* do diretório recentemente descompactado para o diretório *de ativos.*</span><span class="sxs-lookup"><span data-stu-id="a52c6-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="a52c6-190">Criar classes de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="a52c6-190">Create input and output classes</span></span>

1. <span data-ttu-id="a52c6-191">Abra o *arquivo Program.cs* e `using` substitua as instruções existentes na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="a52c6-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="a52c6-192">Abaixo `Program` da classe em *Program.cs,* crie uma classe chamada `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="a52c6-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="a52c6-193">Esta classe é usada para representar os dados inicialmente carregados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="a52c6-194">`ImageData`contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a52c6-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="a52c6-195">`ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="a52c6-196">`Label`é a categoria a que a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="a52c6-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="a52c6-197">Este é o valor para prever.</span><span class="sxs-lookup"><span data-stu-id="a52c6-197">This is the value to predict.</span></span>

1. <span data-ttu-id="a52c6-198">Crie classes para seus dados de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="a52c6-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="a52c6-199">Abaixo `ImageData` da classe, defina o esquema de seus `ModelInput`dados de entrada em uma nova classe chamada .</span><span class="sxs-lookup"><span data-stu-id="a52c6-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="a52c6-200">`ModelInput`contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a52c6-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="a52c6-201">`Image`é `byte[]` a representação da imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="a52c6-202">O modelo espera que os dados de imagem sejam desse tipo para treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="a52c6-203">`LabelAsKey`é a representação numérica `Label`do .</span><span class="sxs-lookup"><span data-stu-id="a52c6-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="a52c6-204">`ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="a52c6-205">`Label`é a categoria a que a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="a52c6-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="a52c6-206">Este é o valor para prever.</span><span class="sxs-lookup"><span data-stu-id="a52c6-206">This is the value to predict.</span></span>

        <span data-ttu-id="a52c6-207">Somente `Image` `LabelAsKey` e são usados para treinar o modelo e fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="a52c6-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="a52c6-208">As `ImagePath` `Label` propriedades e propriedades são mantidas por conveniência para acessar o nome e categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="a52c6-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="a52c6-209">Em seguida, `ModelInput` abaixo da classe, defina o esquema de `ModelOutput`seus dados de saída em uma nova classe chamada .</span><span class="sxs-lookup"><span data-stu-id="a52c6-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="a52c6-210">`ModelOutput`contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a52c6-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="a52c6-211">`ImagePath`é o caminho totalmente qualificado onde a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="a52c6-212">`Label`é a categoria original a que a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="a52c6-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="a52c6-213">Este é o valor para prever.</span><span class="sxs-lookup"><span data-stu-id="a52c6-213">This is the value to predict.</span></span>
        - <span data-ttu-id="a52c6-214">`PredictedLabel`é o valor previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="a52c6-215">Semelhante `ModelInput`a , `PredictedLabel` apenas o é necessário para fazer previsões, uma vez que contém a previsão feita pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="a52c6-216">As `ImagePath` `Label` propriedades e propriedades são retidas para conveniência para acessar o nome e categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="a52c6-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="a52c6-217">Criar diretório de espaço de trabalho</span><span class="sxs-lookup"><span data-stu-id="a52c6-217">Create workspace directory</span></span>

<span data-ttu-id="a52c6-218">Quando os dados de treinamento e validação não mudam com frequência, é uma boa prática armazenar os valores de gargalo computados para outras corridas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="a52c6-219">Em seu projeto, crie um novo diretório chamado *workspace* `.pb` para armazenar os valores de gargalo computados e a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="a52c6-220">Defina caminhos e inicialize variáveis</span><span class="sxs-lookup"><span data-stu-id="a52c6-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="a52c6-221">Dentro `Main` do método, defina a localização de `.pb` seus ativos, valores de gargalo computados e versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="a52c6-222">Inicialize `mlContext` a variável com uma nova instância do [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="a52c6-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="a52c6-223">A classe [MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações ML.NET, e a inicialização do mlContext cria um novo ambiente ML.NET que pode ser compartilhado entre os objetos do fluxo de trabalho de criação de modelos.</span><span class="sxs-lookup"><span data-stu-id="a52c6-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a52c6-224">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a52c6-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a52c6-225">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="a52c6-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="a52c6-226">Criar método utilitário de carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="a52c6-226">Create data loading utility method</span></span>

<span data-ttu-id="a52c6-227">As imagens são armazenadas em dois subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="a52c6-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="a52c6-228">Antes de carregar os dados, ele precisa `ImageData` ser formatado em uma lista de objetos.</span><span class="sxs-lookup"><span data-stu-id="a52c6-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="a52c6-229">Para isso, crie `LoadImagesFromDirectory` o método `Main` abaixo do método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="a52c6-230">Dentro `LoadImagesDirectory` do adicionar o seguinte código para obter todos os caminhos de arquivo dos subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="a52c6-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="a52c6-231">Em seguida, iterar através de `foreach` cada um dos arquivos usando uma declaração.</span><span class="sxs-lookup"><span data-stu-id="a52c6-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="a52c6-232">Dentro `foreach` da declaração, verifique se as extensões de arquivo estão suportadas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="a52c6-233">A API de classificação de imagem suporta formatos JPEG e PNG.</span><span class="sxs-lookup"><span data-stu-id="a52c6-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="a52c6-234">Então, pegue a etiqueta para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-234">Then, get the label for the file.</span></span> <span data-ttu-id="a52c6-235">Se `useFolderNameAsLabel` o parâmetro estiver `true`definido como , então o diretório pai onde o arquivo é salvo é usado como o rótulo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="a52c6-236">Caso contrário, espera que o rótulo seja um prefixo do nome do arquivo ou do próprio nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="a52c6-237">Finalmente, crie uma `ModelInput`nova instância de .</span><span class="sxs-lookup"><span data-stu-id="a52c6-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="a52c6-238">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="a52c6-238">Prepare the data</span></span>

1. <span data-ttu-id="a52c6-239">De volta `Main` ao método, use o `LoadFromDirectory` método utilitário para obter a lista de imagens usadas para treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="a52c6-240">Em seguida, carregue [`IDataView`](xref:Microsoft.ML.IDataView) as [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) imagens em um uso do método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="a52c6-241">Os dados são carregados na ordem em que foram lidos dos diretórios.</span><span class="sxs-lookup"><span data-stu-id="a52c6-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="a52c6-242">Para equilibrar os dados, embaralhe-os usando o [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="a52c6-243">Os modelos de aprendizado de máquina esperam que a entrada seja em formato numérico.</span><span class="sxs-lookup"><span data-stu-id="a52c6-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="a52c6-244">Portanto, alguns pré-processamentos precisam ser feitos nos dados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="a52c6-245">Crie [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) uma forma [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) de `LoadRawImageBytes` transformação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="a52c6-246">A `MapValueToKey` transformação pega o `Label` valor categórico na coluna, `KeyType` converte-a em um `LabelAsKey`valor numérico e armazena-a em uma nova coluna chamada .</span><span class="sxs-lookup"><span data-stu-id="a52c6-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="a52c6-247">O `LoadImages` leva os `ImagePath` valores da `imageFolder` coluna junto com o parâmetro para carregar imagens para treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="a52c6-248">Use [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) o método para aplicar `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) os [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) dados ao método [`IDataView`](xref:Microsoft.ML.IDataView) seguido, que retorna um contendo os dados pré-processados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="a52c6-249">Para treinar um modelo, é importante ter um conjunto de dados de treinamento, bem como um conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="a52c6-250">O modelo é treinado no conjunto de treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-250">The model is trained on the training set.</span></span> <span data-ttu-id="a52c6-251">O quão bem ele faz previsões sobre dados invisíveis é medido pelo desempenho em relação ao conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="a52c6-252">Com base nos resultados desse desempenho, o modelo faz ajustes no que aprendeu em um esforço para melhorar.</span><span class="sxs-lookup"><span data-stu-id="a52c6-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="a52c6-253">O conjunto de validação pode vir da divisão do conjunto de dados original ou de outra fonte que já foi reservada para este fim.</span><span class="sxs-lookup"><span data-stu-id="a52c6-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="a52c6-254">Neste caso, o conjunto de dados pré-processado é dividido em conjuntos de treinamento, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="a52c6-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="a52c6-255">A amostra de código acima realiza duas divisões.</span><span class="sxs-lookup"><span data-stu-id="a52c6-255">The code sample above performs two splits.</span></span> <span data-ttu-id="a52c6-256">Primeiro, os dados pré-processados são divididos e 70% são usados para treinamento, enquanto os 30% restantes são usados para validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="a52c6-257">Em seguida, o conjunto de validação de 30% é dividido em conjuntos de validação e teste onde 90% é usado para validação e 10% é usado para testes.</span><span class="sxs-lookup"><span data-stu-id="a52c6-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="a52c6-258">Uma maneira de pensar sobre o propósito dessas partições de dados é fazer um exame.</span><span class="sxs-lookup"><span data-stu-id="a52c6-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="a52c6-259">Ao estudar para um exame, você revisa suas anotações, livros ou outros recursos para obter uma compreensão sobre os conceitos que estão no exame.</span><span class="sxs-lookup"><span data-stu-id="a52c6-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="a52c6-260">É para isso que é o trem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-260">This is what the train set is for.</span></span> <span data-ttu-id="a52c6-261">Então, você pode fazer um exame simulado para validar seu conhecimento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="a52c6-262">É aqui que o conjunto de validação é útil.</span><span class="sxs-lookup"><span data-stu-id="a52c6-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="a52c6-263">Você quer verificar se você tem uma boa compreensão dos conceitos antes de fazer o exame real.</span><span class="sxs-lookup"><span data-stu-id="a52c6-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="a52c6-264">Com base nesses resultados, você toma nota do que você errou ou não entendeu bem e incorpora suas mudanças à medida que você revisa para o exame real.</span><span class="sxs-lookup"><span data-stu-id="a52c6-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="a52c6-265">Finalmente, você faz o exame.</span><span class="sxs-lookup"><span data-stu-id="a52c6-265">Finally, you take the exam.</span></span> <span data-ttu-id="a52c6-266">É para isso que o conjunto de testes é usado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-266">This is what the test set is used for.</span></span> <span data-ttu-id="a52c6-267">Você nunca viu as questões que estão no exame e agora usa o que aprendeu com o treinamento e validação para aplicar seus conhecimentos à tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="a52c6-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="a52c6-268">Atribuir as partições seus respectivos valores para os dados de trem, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="a52c6-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="a52c6-269">Defina o pipeline de treinamento</span><span class="sxs-lookup"><span data-stu-id="a52c6-269">Define the training pipeline</span></span>

<span data-ttu-id="a52c6-270">O treinamento de modelo consiste em alguns passos.</span><span class="sxs-lookup"><span data-stu-id="a52c6-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="a52c6-271">Primeiro, a API de classificação de imagem é usada para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="a52c6-272">Em seguida, os rótulos `PredictedLabel` codificados na coluna são convertidos `MapKeyToValue` de volta ao seu valor categórico original usando a transformação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="a52c6-273">Crie uma nova variável para armazenar um conjunto `ImageClassificationTrainer`de parâmetros necessários e opcionais para um .</span><span class="sxs-lookup"><span data-stu-id="a52c6-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="a52c6-274">Um `ImageClassificationTrainer` toma vários parâmetros opcionais:</span><span class="sxs-lookup"><span data-stu-id="a52c6-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="a52c6-275">`FeatureColumnName`é a coluna que é usada como entrada para o modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="a52c6-276">`LabelColumnName`é a coluna para o valor prever.</span><span class="sxs-lookup"><span data-stu-id="a52c6-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="a52c6-277">`ValidationSet`é [`IDataView`](xref:Microsoft.ML.IDataView) a contém os dados de validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="a52c6-278">`Arch`define qual das arquiteturas de modelo pré-treinadas usar.</span><span class="sxs-lookup"><span data-stu-id="a52c6-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="a52c6-279">Este tutorial usa a variante de 101 camadas do modelo ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="a52c6-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="a52c6-280">`MetricsCallback`liga uma função para acompanhar o progresso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="a52c6-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="a52c6-281">`TestOnTrainSet`diz ao modelo para medir o desempenho em relação ao conjunto de treinamento quando não há um conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="a52c6-282">`ReuseTrainSetBottleneckCachedValues`informa o modelo se deve usar os valores armazenados em cache a partir da fase de gargalo em corridas subseqüentes.</span><span class="sxs-lookup"><span data-stu-id="a52c6-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="a52c6-283">A fase de gargalo é um cálculo de passagem única que é computacionalmente intensivo na primeira vez que é realizado.</span><span class="sxs-lookup"><span data-stu-id="a52c6-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="a52c6-284">Se os dados de treinamento não mudarem e você quiser experimentar usando um número diferente de épocas ou tamanho de lote, usar os valores armazenados reduz significativamente o tempo necessário para treinar um modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="a52c6-285">`ReuseValidationSetBottleneckCachedValues`é semelhante `ReuseTrainSetBottleneckCachedValues` apenas que, neste caso, é para o conjunto de dados de validação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="a52c6-286">`WorkspacePath`define o diretório onde armazenar os valores `.pb` de gargalo computados e a versão do modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="a52c6-287">Defina [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) o pipeline de treinamento `mapLabelEstimator` que `ImageClassificationTrainer`consiste tanto no e no .</span><span class="sxs-lookup"><span data-stu-id="a52c6-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="a52c6-288">Use [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) o método para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="a52c6-289">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="a52c6-289">Use the model</span></span>

<span data-ttu-id="a52c6-290">Agora que você treinou seu modelo, é hora de usá-lo para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="a52c6-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="a52c6-291">Abaixo `Main` do método, crie um `OutputPrediction` novo método de utilidade chamado para exibir informações de previsão no console.</span><span class="sxs-lookup"><span data-stu-id="a52c6-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="a52c6-292">Classifique uma única imagem</span><span class="sxs-lookup"><span data-stu-id="a52c6-292">Classify a single image</span></span>

1. <span data-ttu-id="a52c6-293">Adicione um novo `ClassifySingleImage` método `Main` chamado abaixo do método para fazer e produzir uma única previsão de imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="a52c6-294">Crie [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) um `ClassifySingleImage` dentro do método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="a52c6-295">A [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você passe e, em seguida, execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="a52c6-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="a52c6-296">Para acessar `ModelInput` uma única `data` [`IDataView`](xref:Microsoft.ML.IDataView) instância, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) converta-a em um usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e, em seguida, obtenha a primeira observação.</span><span class="sxs-lookup"><span data-stu-id="a52c6-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="a52c6-297">Use [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) o método para classificar a imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="a52c6-298">Saída a previsão para `OutputPrediction` o console com o método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="a52c6-299">Dentro `Main` do método, ligue `ClassifySingleImage` usando o conjunto de testes de imagens.</span><span class="sxs-lookup"><span data-stu-id="a52c6-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="a52c6-300">Classificar várias imagens</span><span class="sxs-lookup"><span data-stu-id="a52c6-300">Classify multiple images</span></span>

1. <span data-ttu-id="a52c6-301">Adicione um novo `ClassifyImages` método `ClassifySingleImage` chamado abaixo do método para fazer e produzir várias previsões de imagem.</span><span class="sxs-lookup"><span data-stu-id="a52c6-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="a52c6-302">Crie [`IDataView`](xref:Microsoft.ML.IDataView) uma contendo as previsões usando o [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) método.</span><span class="sxs-lookup"><span data-stu-id="a52c6-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="a52c6-303">Adicione o seguinte código dentro do método `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="a52c6-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="a52c6-304">A fim de iterar sobre `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) as [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) previsões, converta-o em um usando o [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) método e, em seguida, obter as primeiras 10 observações.</span><span class="sxs-lookup"><span data-stu-id="a52c6-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="a52c6-305">Iterar e produzir os rótulos originais e previstos para as previsões.</span><span class="sxs-lookup"><span data-stu-id="a52c6-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="a52c6-306">Finalmente, dentro `Main` do `ClassifyImages` método, ligue usando o conjunto de testes de imagens.</span><span class="sxs-lookup"><span data-stu-id="a52c6-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="a52c6-307">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="a52c6-307">Run the application</span></span>

<span data-ttu-id="a52c6-308">Execute seu aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a52c6-308">Run your console app.</span></span> <span data-ttu-id="a52c6-309">A saída deve ser semelhante à abaixo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-309">The output should be similar to that below.</span></span> <span data-ttu-id="a52c6-310">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="a52c6-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="a52c6-311">Para a brevidade, a saída foi condensada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="a52c6-312">**Fase de gargalo**</span><span class="sxs-lookup"><span data-stu-id="a52c6-312">**Bottleneck phase**</span></span>

<span data-ttu-id="a52c6-313">Nenhum valor é impresso para o nome da imagem `byte[]` porque as imagens são carregadas como uma, portanto, não há nome de imagem para exibir.</span><span class="sxs-lookup"><span data-stu-id="a52c6-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="a52c6-314">**Fase de treinamento**</span><span class="sxs-lookup"><span data-stu-id="a52c6-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="a52c6-315">**Classificar a saída de imagens**</span><span class="sxs-lookup"><span data-stu-id="a52c6-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="a52c6-316">Após a inspeção da imagem *7001-220.jpg,* você pode ver que ela de fato não está rachada.</span><span class="sxs-lookup"><span data-stu-id="a52c6-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Imagem do conjunto de dados SDNET2018 usada para previsão](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="a52c6-318">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="a52c6-318">Congratulations!</span></span> <span data-ttu-id="a52c6-319">Agora você construiu com sucesso um modelo de aprendizagem profunda para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="a52c6-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="a52c6-320">Melhorar o modelo</span><span class="sxs-lookup"><span data-stu-id="a52c6-320">Improve the model</span></span>

<span data-ttu-id="a52c6-321">Se você não está satisfeito com os resultados do seu modelo, você pode tentar melhorar seu desempenho, tentando algumas das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="a52c6-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="a52c6-322">**Mais Dados**: Quanto mais exemplos um modelo aprende, melhor ele se sai.</span><span class="sxs-lookup"><span data-stu-id="a52c6-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="a52c6-323">Baixe o [conjunto de dados SDNET2018 completo](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) e use-o para treinar.</span><span class="sxs-lookup"><span data-stu-id="a52c6-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="a52c6-324">**Aumentar os dados**: Uma técnica comum para adicionar variedade aos dados é aumentar os dados tirando uma imagem e aplicando diferentes transformações (girar, virar, mudar, cortar).</span><span class="sxs-lookup"><span data-stu-id="a52c6-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="a52c6-325">Isso adiciona exemplos mais variados para o modelo aprender.</span><span class="sxs-lookup"><span data-stu-id="a52c6-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="a52c6-326">**Trem por mais tempo**: Quanto mais você treinar, mais sintonizado será o modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="a52c6-327">Aumentar o número de épocas pode melhorar o desempenho do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="a52c6-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="a52c6-328">**Experimente com os hiperparâmetros**: Além dos parâmetros utilizados neste tutorial, outros parâmetros podem ser ajustados para potencialmente melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="a52c6-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="a52c6-329">Alterar a taxa de aprendizado, que determina a magnitude das atualizações feitas no modelo após cada época pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="a52c6-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="a52c6-330">**Use uma arquitetura de modelo diferente**: Dependendo de como seus dados se parecem, o modelo que pode melhor aprender suas características pode diferir.</span><span class="sxs-lookup"><span data-stu-id="a52c6-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="a52c6-331">Se você não está satisfeito com o desempenho do seu modelo, tente mudar a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="a52c6-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a52c6-332">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="a52c6-332">Additional Resources</span></span>

- <span data-ttu-id="a52c6-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="a52c6-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a52c6-334">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a52c6-334">Next steps</span></span>

<span data-ttu-id="a52c6-335">Neste tutorial, você aprendeu como construir um modelo de aprendizagem profunda personalizado usando o aprendizado de transferência, um modelo de classificação de imagem pré-treinado TensorFlow e a API de classificação de imagem ML.NET para classificar imagens de superfícies de concreto como rachadas ou não rachadas.</span><span class="sxs-lookup"><span data-stu-id="a52c6-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="a52c6-336">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="a52c6-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a52c6-337">Detecção de objetos</span><span class="sxs-lookup"><span data-stu-id="a52c6-337">Object Detection</span></span>](object-detection-onnx.md)
