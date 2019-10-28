---
title: 'Tutorial: inspeção visual automatizada usando o aprendizado de transferência'
description: Este tutorial ilustra como usar o aprendizado de transferência para treinar um modelo de aprendizado profundo do TensorFlow no ML.NET usando a API de detecção de imagem para classificar imagens de superfícies concretas como rachadas ou não rachadas.
author: luisquintanilla
ms.author: luquinta
ms.date: 10/25/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b8aec80134188811eb80ad1394e5a64d65a3c6f0
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961983"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="51052-103">Tutorial: inspeção visual automatizada usando o aprendizado de transferência com a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="51052-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="51052-104">Saiba como treinar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow pretreinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.</span><span class="sxs-lookup"><span data-stu-id="51052-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

> [!NOTE]
> <span data-ttu-id="51052-105">Este tutorial usa uma versão de visualização da API de classificação de imagem ML.NET.</span><span class="sxs-lookup"><span data-stu-id="51052-105">This tutorial uses a preview version of the ML.NET Image Classification API.</span></span>

<span data-ttu-id="51052-106">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="51052-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="51052-107">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="51052-107">Understand the problem</span></span>
> - <span data-ttu-id="51052-108">Saiba mais sobre a API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="51052-108">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="51052-109">Entender o modelo pretreinado</span><span class="sxs-lookup"><span data-stu-id="51052-109">Understand the pretrained model</span></span>
> - <span data-ttu-id="51052-110">Usar o aprendizado de transferência para treinar um modelo de classificação de imagem TensorFlow personalizado</span><span class="sxs-lookup"><span data-stu-id="51052-110">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="51052-111">Classificar imagens com o modelo personalizado</span><span class="sxs-lookup"><span data-stu-id="51052-111">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="51052-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="51052-112">Prerequisites</span></span>

- <span data-ttu-id="51052-113">[Visual Studio 2017 15.6 ou posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" instalada.</span><span class="sxs-lookup"><span data-stu-id="51052-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="51052-114">Visão geral do exemplo de aprendizado de transferência de classificação de imagem</span><span class="sxs-lookup"><span data-stu-id="51052-114">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="51052-115">Este exemplo é um C# aplicativo de console .NET Core que classifica imagens usando um modelo de TensorFlow de aprendizado profundo pretreinado.</span><span class="sxs-lookup"><span data-stu-id="51052-115">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="51052-116">O código para este exemplo pode ser encontrado no [repositório dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="51052-116">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="51052-117">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="51052-117">Understand the problem</span></span>

<span data-ttu-id="51052-118">A classificação de imagem é um problema de pesquisa Visual computacional.</span><span class="sxs-lookup"><span data-stu-id="51052-118">Image classification is a computer vision problem.</span></span> <span data-ttu-id="51052-119">A classificação de imagem usa uma imagem como entrada e a categoriza em uma classe prescrita.</span><span class="sxs-lookup"><span data-stu-id="51052-119">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="51052-120">Alguns cenários em que a classificação de imagem é útil incluem:</span><span class="sxs-lookup"><span data-stu-id="51052-120">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="51052-121">Reconhecimento de rosto</span><span class="sxs-lookup"><span data-stu-id="51052-121">Facial recognition</span></span>
- <span data-ttu-id="51052-122">Detecção de emoções</span><span class="sxs-lookup"><span data-stu-id="51052-122">Emotion detection</span></span>
- <span data-ttu-id="51052-123">Diagnóstico médico</span><span class="sxs-lookup"><span data-stu-id="51052-123">Medical diagnosis</span></span>
- <span data-ttu-id="51052-124">Detecção de ponto de referência</span><span class="sxs-lookup"><span data-stu-id="51052-124">Landmark detection</span></span>

<span data-ttu-id="51052-125">Este tutorial treina um modelo de classificação de imagem personalizada para executar a inspeção visual automatizada de decks de ponte para identificar estruturas que estão danificadas por rachaduras.</span><span class="sxs-lookup"><span data-stu-id="51052-125">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="51052-126">API de classificação de imagem ML.NET</span><span class="sxs-lookup"><span data-stu-id="51052-126">ML.NET Image Classification API</span></span>

<span data-ttu-id="51052-127">O ML.NET fornece várias maneiras de executar a classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="51052-127">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="51052-128">Este tutorial aplica-se ao aprendizado de transferência usando a API de classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="51052-128">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="51052-129">A API de classificação de imagem usa [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET), uma biblioteca de nível baixo que fornece C# associações para a API TensorFlow C++ .</span><span class="sxs-lookup"><span data-stu-id="51052-129">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="51052-130">O que é o aprendizado por transferência?</span><span class="sxs-lookup"><span data-stu-id="51052-130">What is transfer learning?</span></span>

<span data-ttu-id="51052-131">O aprendizado de transferência aplica o conhecimento obtido da solução de um problema para outro problema relacionado.</span><span class="sxs-lookup"><span data-stu-id="51052-131">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="51052-132">Treinar um modelo de aprendizado profundo do zero exige a definição de vários parâmetros, uma grande quantidade de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="51052-132">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="51052-133">Usar um modelo pretreinado junto com o aprendizado de transferência permite que você Modele o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-133">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span> 

## <a name="training-process"></a><span data-ttu-id="51052-134">Processo de treinamento</span><span class="sxs-lookup"><span data-stu-id="51052-134">Training process</span></span>

<span data-ttu-id="51052-135">A API de classificação de imagem inicia o processo de treinamento carregando um modelo de TensorFlow pré-treinado.</span><span class="sxs-lookup"><span data-stu-id="51052-135">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="51052-136">O processo de treinamento consiste em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="51052-136">The training process consists of two steps:</span></span>

1. <span data-ttu-id="51052-137">Fase de afunilamento</span><span class="sxs-lookup"><span data-stu-id="51052-137">Bottleneck phase</span></span>
2. <span data-ttu-id="51052-138">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="51052-138">Training phase</span></span>

![Etapas de treinamento](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="51052-140">Fase de afunilamento</span><span class="sxs-lookup"><span data-stu-id="51052-140">Bottleneck phase</span></span>

<span data-ttu-id="51052-141">Durante a fase de afunilamento, o conjunto de imagens de treinamento é carregado e os valores de pixel são usados como entrada, ou recursos, para as camadas congeladas do modelo pretreinado.</span><span class="sxs-lookup"><span data-stu-id="51052-141">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="51052-142">As camadas congeladas incluem todas as camadas na rede neural até a camada penúltima, informalmente conhecida como a camada de afunilamento.</span><span class="sxs-lookup"><span data-stu-id="51052-142">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="51052-143">Essas camadas são referidas como congeladas porque nenhum treinamento ocorrerá nessas camadas e as operações são passagem.</span><span class="sxs-lookup"><span data-stu-id="51052-143">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="51052-144">Elas estão nessas camadas congeladas onde os padrões de nível inferior que ajudam um modelo diferenciar entre as diferentes classes são computadas.</span><span class="sxs-lookup"><span data-stu-id="51052-144">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="51052-145">Quanto maior o número de camadas, mais intensivamente essa etapa é computada.</span><span class="sxs-lookup"><span data-stu-id="51052-145">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="51052-146">Felizmente, como esse é um cálculo único, os resultados podem ser armazenados em cache e usados em execuções posteriores ao experimentar parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="51052-146">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="51052-147">Fase de treinamento</span><span class="sxs-lookup"><span data-stu-id="51052-147">Training phase</span></span>

<span data-ttu-id="51052-148">Depois que os valores de saída da fase de afunilamento são computados, eles são usados como entrada para treinar novamente a camada final do modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-148">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="51052-149">Esse processo é iterativo e é executado para o número de vezes especificado por parâmetros de modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-149">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="51052-150">Durante cada execução, a perda e a precisão são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="51052-150">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="51052-151">Em seguida, os ajustes apropriados são feitos para melhorar o modelo com o objetivo de minimizar a perda e maximizar a precisão.</span><span class="sxs-lookup"><span data-stu-id="51052-151">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="51052-152">Quando o treinamento for concluído, dois formatos de modelo serão gerados.</span><span class="sxs-lookup"><span data-stu-id="51052-152">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="51052-153">Um deles é a versão `.pb` do modelo e o outro é a versão serializada `.zip` ML.NET do modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-153">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="51052-154">Ao trabalhar em ambientes com suporte do ML.NET, é recomendável usar a versão `.zip` do modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-154">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="51052-155">No entanto, em ambientes em que não há suporte para ML.NET, você tem a opção de usar a versão `.pb`.</span><span class="sxs-lookup"><span data-stu-id="51052-155">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="51052-156">Entender o modelo pretreinado</span><span class="sxs-lookup"><span data-stu-id="51052-156">Understand the pretrained model</span></span>

<span data-ttu-id="51052-157">O modelo pretreinado usado neste tutorial é a variante de camada 101 do modelo de rede residual (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="51052-157">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="51052-158">O modelo original é treinado para classificar imagens em milhares de categorias.</span><span class="sxs-lookup"><span data-stu-id="51052-158">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="51052-159">O modelo usa como entrada uma imagem de tamanho 224 x 224 e gera as probabilidades de classe para cada uma das classes em que é treinado.</span><span class="sxs-lookup"><span data-stu-id="51052-159">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="51052-160">Parte desse modelo é usada para treinar um novo modelo usando imagens personalizadas para fazer previsões entre duas classes.</span><span class="sxs-lookup"><span data-stu-id="51052-160">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span> 

## <a name="create-console-application"></a><span data-ttu-id="51052-161">Criar aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="51052-161">Create console application</span></span>

<span data-ttu-id="51052-162">Agora que você tem uma compreensão geral do aprendizado de transferência e da API de classificação de imagem, é hora de criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51052-162">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="51052-163">Crie um  **C# aplicativo de console do .NET Core** chamado "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="51052-163">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="51052-164">Instale o pacote NuGet **Microsoft.ml 1.4.0-Preview2** :</span><span class="sxs-lookup"><span data-stu-id="51052-164">Install the **Microsoft.ML 1.4.0-preview2** NuGet Package:</span></span>
    1. <span data-ttu-id="51052-165">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="51052-165">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="51052-166">Escolha "nuget.org" como a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="51052-166">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="51052-167">Selecione a guia **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="51052-167">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="51052-168">Marque a caixa de seleção **incluir pré-lançamento** .</span><span class="sxs-lookup"><span data-stu-id="51052-168">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="51052-169">Procure **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="51052-169">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="51052-170">Selecione o botão **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="51052-170">Select the **Install** button.</span></span>
    1. <span data-ttu-id="51052-171">Selecione o botão **OK** na caixa de diálogo **Visualizar Alterações** e selecione o botão **Aceito** na caixa de diálogo **Aceitação da Licença**, se concordar com o termos de licença para os pacotes listados.</span><span class="sxs-lookup"><span data-stu-id="51052-171">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="51052-172">Repita essas etapas para **Microsoft. ml. DNN 0.16.0-Preview2** e **Microsoft. ml. ImageAnalytics 1.4.0-Preview2**.</span><span class="sxs-lookup"><span data-stu-id="51052-172">Repeat these steps for **Microsoft.ML.Dnn 0.16.0-preview2** and **Microsoft.ML.ImageAnalytics 1.4.0-preview2**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="51052-173">Preparar e compreender os dados</span><span class="sxs-lookup"><span data-stu-id="51052-173">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="51052-174">Os conjuntos de valores para este tutorial são de Maguire, Marc; Dorafshan, Sattar; e Thomas, Robert J., "SDNET2018: um conjunto de imagem de quebra concreta para aplicativos de Machine Learning" (2018).</span><span class="sxs-lookup"><span data-stu-id="51052-174">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="51052-175">Procurar todos os conjuntos de valores.</span><span class="sxs-lookup"><span data-stu-id="51052-175">Browse all Datasets.</span></span> <span data-ttu-id="51052-176">Papel 48.</span><span class="sxs-lookup"><span data-stu-id="51052-176">Paper 48.</span></span> <span data-ttu-id="51052-177">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="51052-177">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="51052-178">SDNET2018 é um conjunto de uma imagem que contém anotações para estruturas concretas rachadas e não rachadas (baralhos de ponte, paredes e Pavement).</span><span class="sxs-lookup"><span data-stu-id="51052-178">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span> 

![Amostras de baralho da ponte do conjunto de SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="51052-180">Os dados são organizados em três subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="51052-180">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="51052-181">D contém imagens do deck de ponte</span><span class="sxs-lookup"><span data-stu-id="51052-181">D contains bridge deck images</span></span>
- <span data-ttu-id="51052-182">P contém imagens Pavement</span><span class="sxs-lookup"><span data-stu-id="51052-182">P contains pavement images</span></span>
- <span data-ttu-id="51052-183">W contém imagens de parede</span><span class="sxs-lookup"><span data-stu-id="51052-183">W contains wall images</span></span>

<span data-ttu-id="51052-184">Cada um desses subdiretórios contém dois subdiretórios prefixais adicionais:</span><span class="sxs-lookup"><span data-stu-id="51052-184">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="51052-185">C é o prefixo usado para superfícies rachadas</span><span class="sxs-lookup"><span data-stu-id="51052-185">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="51052-186">U é o prefixo usado para superfícies não decifradas</span><span class="sxs-lookup"><span data-stu-id="51052-186">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="51052-187">Neste tutorial, somente imagens de baralho de ponte são usadas.</span><span class="sxs-lookup"><span data-stu-id="51052-187">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="51052-188">Baixe o [conjunto](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) de e descompacte.</span><span class="sxs-lookup"><span data-stu-id="51052-188">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="51052-189">Crie um diretório chamado "ativos" em seu projeto para salvar os arquivos do conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="51052-189">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="51052-190">Copie os subdiretórios *CD* e *UD* do diretório recentemente descompactado para o diretório de *ativos* .</span><span class="sxs-lookup"><span data-stu-id="51052-190">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="51052-191">Criar classes de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="51052-191">Create input and output classes</span></span>

1. <span data-ttu-id="51052-192">Abra o arquivo *Program.cs* e substitua as instruções de `using` existentes na parte superior do arquivo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="51052-192">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="51052-193">Abaixo da classe `Program` em *Program.cs*, crie uma classe chamada `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="51052-193">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="51052-194">Essa classe é usada para representar os dados carregados inicialmente.</span><span class="sxs-lookup"><span data-stu-id="51052-194">This class is used to represent the initially loaded data.</span></span> 

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L135-L140)]

    <span data-ttu-id="51052-195">`ImageData` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="51052-195">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="51052-196">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="51052-196">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="51052-197">`Label` é a categoria à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="51052-197">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="51052-198">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="51052-198">This is the value to predict.</span></span>

1. <span data-ttu-id="51052-199">Criar classes para os dados de entrada e saída</span><span class="sxs-lookup"><span data-stu-id="51052-199">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="51052-200">Abaixo da classe `ImageData`, defina o esquema dos dados de entrada em uma nova classe chamada `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="51052-200">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L142-L151)]

        <span data-ttu-id="51052-201">`ModelInput` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="51052-201">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="51052-202">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="51052-202">`ImagePath` is the fully qualified path where the image is stored.</span></span> 
        - <span data-ttu-id="51052-203">`Label` é a categoria à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="51052-203">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="51052-204">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="51052-204">This is the value to predict.</span></span>
        - <span data-ttu-id="51052-205">`Image` é a representação `byte[]` da imagem.</span><span class="sxs-lookup"><span data-stu-id="51052-205">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="51052-206">O modelo espera que os dados de imagem sejam desse tipo para treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-206">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="51052-207">`LabelAsKey` é a representação numérica do `Label`.</span><span class="sxs-lookup"><span data-stu-id="51052-207">`LabelAsKey` is the numerical representation of the `Label`.</span></span> 

        <span data-ttu-id="51052-208">Somente `Image` e `LabelAsKey` são usados para treinar o modelo e fazer previsões.</span><span class="sxs-lookup"><span data-stu-id="51052-208">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="51052-209">As propriedades `ImagePath` e `Label` são mantidas por conveniência para acessar o nome e a categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="51052-209">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="51052-210">Em seguida, abaixo da classe `ModelInput`, defina o esquema dos dados de saída em uma nova classe chamada `ModelOutput`.</span><span class="sxs-lookup"><span data-stu-id="51052-210">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span> 

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L153-L160)]

        <span data-ttu-id="51052-211">`ModelOutput` contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="51052-211">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="51052-212">`ImagePath` é o caminho totalmente qualificado em que a imagem é armazenada.</span><span class="sxs-lookup"><span data-stu-id="51052-212">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="51052-213">`Label` é a categoria original à qual a imagem pertence.</span><span class="sxs-lookup"><span data-stu-id="51052-213">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="51052-214">Esse é o valor a prever.</span><span class="sxs-lookup"><span data-stu-id="51052-214">This is the value to predict.</span></span> 
        - <span data-ttu-id="51052-215">`PredictedLabel` é o valor previsto pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-215">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="51052-216">Semelhante à `ModelInput`, somente o `PredictedLabel` é necessário para fazer previsões, pois contém a previsão feita pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-216">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="51052-217">As propriedades `ImagePath` e `Label` são mantidas por conveniência para acessar o nome e a categoria do arquivo de imagem original.</span><span class="sxs-lookup"><span data-stu-id="51052-217">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="51052-218">Definir caminhos e inicializar variáveis</span><span class="sxs-lookup"><span data-stu-id="51052-218">Define paths and initialize variables</span></span>

1. <span data-ttu-id="51052-219">Dentro do método `Main`, defina o local de seus ativos.</span><span class="sxs-lookup"><span data-stu-id="51052-219">Inside the `Main` method, define the location of your assets.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L16)]

1. <span data-ttu-id="51052-220">Em seguida, inicialize a variável `mlContext` com uma nova instância de [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="51052-220">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L18)]

<span data-ttu-id="51052-221">A classe [MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações de ml.net, e a inicialização de MLContext cria um novo ambiente ml.NET que pode ser compartilhado entre os objetos de fluxo de trabalho de criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-221">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="51052-222">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="51052-222">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="51052-223">Carregar os dados</span><span class="sxs-lookup"><span data-stu-id="51052-223">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="51052-224">Criar método de utilitário de carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="51052-224">Create data loading utility method</span></span>

<span data-ttu-id="51052-225">As imagens são armazenadas em dois subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="51052-225">The images are stored in two subdirectories.</span></span> <span data-ttu-id="51052-226">Antes de carregar os dados, ele precisa ser formatado em uma lista de objetos de `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="51052-226">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="51052-227">Para fazer isso, crie o método `LoadImagesFromDirectory` abaixo do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="51052-227">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="51052-228">Dentro do `LoadImagesDirectory` adicione o seguinte código para obter todos os caminhos de arquivo dos subdiretórios:</span><span class="sxs-lookup"><span data-stu-id="51052-228">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L102-L103)]

1. <span data-ttu-id="51052-229">Em seguida, Itere em cada um dos arquivos usando uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="51052-229">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="51052-230">Dentro da instrução `foreach`, verifique se as extensões de arquivo têm suporte.</span><span class="sxs-lookup"><span data-stu-id="51052-230">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="51052-231">A API de classificação de imagem dá suporte aos formatos JPEG e PNG.</span><span class="sxs-lookup"><span data-stu-id="51052-231">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L107-L108)]

1. <span data-ttu-id="51052-232">Em seguida, obtenha o rótulo para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="51052-232">Then, get the label for the file.</span></span> <span data-ttu-id="51052-233">Se o parâmetro `useFolderNameAsLabel` for definido como `true`, o diretório pai onde o arquivo é salvo será usado como o rótulo.</span><span class="sxs-lookup"><span data-stu-id="51052-233">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="51052-234">Caso contrário, ele espera que o rótulo seja um prefixo do nome do arquivo ou o próprio nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="51052-234">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L110-L124)]

1. <span data-ttu-id="51052-235">Por fim, crie uma nova instância do `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="51052-235">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L126-L130)]

### <a name="prepare-the-data"></a><span data-ttu-id="51052-236">Preparar os dados</span><span class="sxs-lookup"><span data-stu-id="51052-236">Prepare the data</span></span>

1. <span data-ttu-id="51052-237">De volta ao método `Main`, use o método utilitário `LoadFromDirectory` para obter a lista de imagens usadas para treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-237">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L20)]

1. <span data-ttu-id="51052-238">Em seguida, carregue as imagens em um [`IDataView`](xref:Microsoft.ML.IDataView) usando o método [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="51052-238">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L22)]    

1. <span data-ttu-id="51052-239">Os dados são carregados na ordem em que foram lidos dos diretórios.</span><span class="sxs-lookup"><span data-stu-id="51052-239">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="51052-240">Para balancear os dados, use a ordem aleatória usando o método [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) .</span><span class="sxs-lookup"><span data-stu-id="51052-240">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L24)]

1. <span data-ttu-id="51052-241">Os modelos de aprendizado de máquina esperam que a entrada esteja em formato numérico.</span><span class="sxs-lookup"><span data-stu-id="51052-241">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="51052-242">Portanto, algum pré-processamento precisa ser feito nos dados antes do treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-242">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="51052-243">Crie uma [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) composta das transformações de [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) e [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) .</span><span class="sxs-lookup"><span data-stu-id="51052-243">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) transforms.</span></span> <span data-ttu-id="51052-244">A transformação `MapValueToKey` usa o valor categórico na coluna `Label`, converte-o em um valor de `KeyType` numérico e o armazena em uma nova coluna chamada `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="51052-244">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="51052-245">O `LoadImages` usa os valores da coluna `ImagePath` junto com o parâmetro `imageFolder` para carregar imagens para treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-245">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span> <span data-ttu-id="51052-246">Definir a `useImageType` como `false` converte as imagens em uma `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="51052-246">Setting the `useImageType` to `false` converts the images into a `byte[]`.</span></span> 

    [!code-csharp [DefinePreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L26-L33)]

1. <span data-ttu-id="51052-247">Use o método [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) para aplicar os dados ao `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) seguido pelo método [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) , que retorna um [`IDataView`](xref:Microsoft.ML.IDataView) contendo os dados previamente processados.</span><span class="sxs-lookup"><span data-stu-id="51052-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="51052-248">Para treinar um modelo, é importante ter um conjunto de um de treinamento, bem como um conjunto de uma validação.</span><span class="sxs-lookup"><span data-stu-id="51052-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="51052-249">O modelo é treinado no conjunto de treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-249">The model is trained on the training set.</span></span> <span data-ttu-id="51052-250">O quão bem ele faz previsões sobre dados não vistos é medido pelo desempenho em relação ao conjunto de validação.</span><span class="sxs-lookup"><span data-stu-id="51052-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="51052-251">Com base nos resultados desse desempenho, o modelo faz ajustes no que ele aprendeu em um esforço para melhorar.</span><span class="sxs-lookup"><span data-stu-id="51052-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="51052-252">O conjunto de validação pode vir de uma divisão do conjunto de seus conjuntos de seus originais ou de outra fonte que já tenha sido reservada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="51052-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="51052-253">Nesse caso, o conjunto de valores previamente processados é dividido em conjuntos de treinamento, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="51052-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="51052-254">O exemplo de código acima executa duas divisões.</span><span class="sxs-lookup"><span data-stu-id="51052-254">The code sample above performs two splits.</span></span> <span data-ttu-id="51052-255">Primeiro, os dados previamente processados são divididos e 70% é usado para treinamento enquanto os 30% restantes são usados para validação.</span><span class="sxs-lookup"><span data-stu-id="51052-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="51052-256">Em seguida, o conjunto de validação de 30% é mais dividido em conjuntos de validação e de teste em que 90% é usado para validação e 10% é usado para teste.</span><span class="sxs-lookup"><span data-stu-id="51052-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span> 

    <span data-ttu-id="51052-257">Uma maneira de pensar sobre a finalidade dessas partições de dados é fazer um exame.</span><span class="sxs-lookup"><span data-stu-id="51052-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="51052-258">Ao estudar um exame, você examina suas notas, livros ou outros recursos para entender os conceitos que estão no exame.</span><span class="sxs-lookup"><span data-stu-id="51052-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="51052-259">É para isso que se trata o conjunto de treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-259">This is what the train set is for.</span></span> <span data-ttu-id="51052-260">Em seguida, você pode fazer um exame fictício para validar seu conhecimento.</span><span class="sxs-lookup"><span data-stu-id="51052-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="51052-261">É aí que o conjunto de validação é útil.</span><span class="sxs-lookup"><span data-stu-id="51052-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="51052-262">Você quer verificar se tem uma boa noção dos conceitos antes de pegar o exame real.</span><span class="sxs-lookup"><span data-stu-id="51052-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="51052-263">Com base nesses resultados, anote o que você obteve errado ou não entendeu bem e incorpore suas alterações ao examinar o exame real.</span><span class="sxs-lookup"><span data-stu-id="51052-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="51052-264">Por fim, você assume o exame.</span><span class="sxs-lookup"><span data-stu-id="51052-264">Finally, you take the exam.</span></span> <span data-ttu-id="51052-265">É para isso que o conjunto de testes é usado.</span><span class="sxs-lookup"><span data-stu-id="51052-265">This is what the test set is used for.</span></span> <span data-ttu-id="51052-266">Você nunca viu as perguntas que estão no exame e agora usa o que aprendeu do treinamento e da validação para aplicar seu conhecimento à tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="51052-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span> 

1. <span data-ttu-id="51052-267">Atribua as partições seus respectivos valores para os dados de treinamento, validação e teste.</span><span class="sxs-lookup"><span data-stu-id="51052-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="51052-268">Definir o pipeline de treinamento</span><span class="sxs-lookup"><span data-stu-id="51052-268">Define the training pipeline</span></span>

<span data-ttu-id="51052-269">O treinamento de modelo consiste em algumas etapas.</span><span class="sxs-lookup"><span data-stu-id="51052-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="51052-270">Primeiro, a API de classificação de imagem é usada para treinar o modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="51052-271">Em seguida, os rótulos codificados na coluna `PredictedLabel` são convertidos de volta para seu valor categórico original usando a transformação `MapKeyToValue`.</span><span class="sxs-lookup"><span data-stu-id="51052-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span> 

1. <span data-ttu-id="51052-272">Defina o pipeline de [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) de treinamento que consiste nas transformações `mapLabelEstimator` e `ImageClassification`.</span><span class="sxs-lookup"><span data-stu-id="51052-272">Define the training [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline that consists of both the `mapLabelEstimator` and the `ImageClassification` transforms.</span></span>

    [!code-csharp [DefineTrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L58)]    

    <span data-ttu-id="51052-273">O estimador de `ImageClassification` usa vários parâmetros:</span><span class="sxs-lookup"><span data-stu-id="51052-273">The `ImageClassification` estimator takes in several parameters:</span></span>

    - <span data-ttu-id="51052-274">`featuresColumnName` é a coluna usada como entrada para o modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-274">`featuresColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="51052-275">`labelColumnName` é a coluna do valor a prever.</span><span class="sxs-lookup"><span data-stu-id="51052-275">`labelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="51052-276">`arch` define qual das arquiteturas de modelo pretreinados usar.</span><span class="sxs-lookup"><span data-stu-id="51052-276">`arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="51052-277">Este tutorial usa a variante de camada 101 do modelo ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="51052-277">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="51052-278">`epoch` especifica o número máximo de iterações em todo o conjunto de todos os processos de treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-278">`epoch` specifies the maximum number of iterations over the entire dataset throughout the training process.</span></span> <span data-ttu-id="51052-279">Quanto maior o número, mais longo o modelo Treina e potencialmente o melhor modelo produzido.</span><span class="sxs-lookup"><span data-stu-id="51052-279">The higher the number, the longer the model trains for and potentially the better model that is produced.</span></span>
    - <span data-ttu-id="51052-280">`batchSize` é o número de amostras a ser usado por vez para treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-280">`batchSize` is the number of samples to use at a time for training.</span></span> <span data-ttu-id="51052-281">Durante uma época, vários lotes iguais ao batchSize são usados para treinar e atualizar o modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-281">During one epoch, multiple batches equal to the batchSize are used to train and update the model.</span></span> <span data-ttu-id="51052-282">Quanto menor o número, menor a memória necessária quando cada lote é processado.</span><span class="sxs-lookup"><span data-stu-id="51052-282">The lower the number, the less memory required when each batch is processed.</span></span>
    - <span data-ttu-id="51052-283">`testOnTrainSet` diz ao modelo para medir o desempenho em relação ao conjunto de treinamento quando nenhum conjunto de validação está presente.</span><span class="sxs-lookup"><span data-stu-id="51052-283">`testOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="51052-284">`metricsCallback` associa uma função para acompanhar o progresso durante o treinamento.</span><span class="sxs-lookup"><span data-stu-id="51052-284">`metricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="51052-285">`validationSet` é a [`IDataView`](xref:Microsoft.ML.IDataView) que contém os dados de validação.</span><span class="sxs-lookup"><span data-stu-id="51052-285">`validationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="51052-286">`reuseTrainSetBottleneckCachedValues` informa ao modelo se os valores armazenados em cache devem ser usados da fase de afunilamento nas execuções subsequentes.</span><span class="sxs-lookup"><span data-stu-id="51052-286">`reuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="51052-287">A fase de afunilamento é uma computação de passagem única que é computacionalmente intensiva na primeira vez em que é executada.</span><span class="sxs-lookup"><span data-stu-id="51052-287">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="51052-288">Se os dados de treinamento não forem alterados e você quiser experimentar o uso de um número diferente de épocas ou do tamanho do lote, usar os valores armazenados em cache reduz significativamente o tempo necessário para treinar um modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-288">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="51052-289">`reuseValidationSetBottleneckCachedValues` é semelhante a `reuseTrainSetBottleneckCachedValues` apenas que, nesse caso, é para o conjunto de conjuntos de validação.</span><span class="sxs-lookup"><span data-stu-id="51052-289">`reuseValidationSetBottleneckCachedValues` is similar to `reuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="51052-290">`disableEarlyStopping` diz ao estimador ImageClassification se deve empregar uma estratégia de interrupção inicial.</span><span class="sxs-lookup"><span data-stu-id="51052-290">`disableEarlyStopping` tells the ImageClassification estimator whether to employ an early stopping strategy.</span></span> <span data-ttu-id="51052-291">Como o modelo pesquisa os valores ideais que o ajudarão a fazer previsões precisas durante o treinamento, o desempenho pode aumentar ou diminuir.</span><span class="sxs-lookup"><span data-stu-id="51052-291">As the model searches for the optimal values that will help it make accurate predictions during training, performance may increase or decrease.</span></span> <span data-ttu-id="51052-292">Por fim, se o modelo atingir a última época, pode ser o caso de que os padrões aprendidos do treinamento sejam subótimos.</span><span class="sxs-lookup"><span data-stu-id="51052-292">Ultimately, if the model reaches the last epoch, it may be the case that the patterns it learned from training are suboptimal.</span></span> <span data-ttu-id="51052-293">A parada inicial dos monitores de treinamento para esses Descartes no desempenho e interrompe o processo de treinamento em um esforço para preservar uma versão ideal do modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-293">Early stopping monitors training for these drops in performance and stops the training process in an effort to preserve an optimal version of the model.</span></span>

1. <span data-ttu-id="51052-294">Use o método [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) para treinar seu modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-294">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L60)]

## <a name="use-the-model"></a><span data-ttu-id="51052-295">Usar o modelo</span><span class="sxs-lookup"><span data-stu-id="51052-295">Use the model</span></span>

<span data-ttu-id="51052-296">Agora que você treinou seu modelo, é hora de usá-lo para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="51052-296">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="51052-297">Abaixo do método `Main`, crie um novo método utilitário chamado `OutputPrediction` para exibir informações de previsão no console do.</span><span class="sxs-lookup"><span data-stu-id="51052-297">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L94-L98)]

### <a name="classify-a-single-image"></a><span data-ttu-id="51052-298">Classificar uma única imagem</span><span class="sxs-lookup"><span data-stu-id="51052-298">Classify a single image</span></span>

1. <span data-ttu-id="51052-299">Adicione um novo método chamado `ClassifySingleImage` abaixo do método `Main` para fazer e gerar uma previsão de imagem única.</span><span class="sxs-lookup"><span data-stu-id="51052-299">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="51052-300">Crie um [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dentro do método `ClassifySingleImage`.</span><span class="sxs-lookup"><span data-stu-id="51052-300">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="51052-301">A [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) é uma API de conveniência, que permite que você passe e execute uma previsão em uma única instância de dados.</span><span class="sxs-lookup"><span data-stu-id="51052-301">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L71)]    

1. <span data-ttu-id="51052-302">Para acessar uma única instância de `ModelInput`, converta o [`IDataView`](xref:Microsoft.ML.IDataView) de `data` em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e, em seguida, obtenha a primeira observação.</span><span class="sxs-lookup"><span data-stu-id="51052-302">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span> 

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="51052-303">Use o método [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) para classificar a imagem.</span><span class="sxs-lookup"><span data-stu-id="51052-303">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="51052-304">Gere a previsão para o console com o método `OutputPrediction`.</span><span class="sxs-lookup"><span data-stu-id="51052-304">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77-L78)]

1. <span data-ttu-id="51052-305">Dentro do método `Main`, chame `ClassifySingleImage` usando o conjunto de teste de imagens.</span><span class="sxs-lookup"><span data-stu-id="51052-305">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

### <a name="classify-multiple-images"></a><span data-ttu-id="51052-306">Classificar várias imagens</span><span class="sxs-lookup"><span data-stu-id="51052-306">Classify multiple images</span></span>

1. <span data-ttu-id="51052-307">Adicione um novo método chamado `ClassifyImages` abaixo do método `ClassifySingleImage` para fazer e gerar várias previsões de imagem.</span><span class="sxs-lookup"><span data-stu-id="51052-307">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="51052-308">Crie um [`IDataView`](xref:Microsoft.ML.IDataView) que contenha as previsões usando o método [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) .</span><span class="sxs-lookup"><span data-stu-id="51052-308">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="51052-309">Adicione o seguinte código dentro do método `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="51052-309">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L83)]

1. <span data-ttu-id="51052-310">Para iterar as previsões, converta o `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) em um [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) usando o método [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) e, em seguida, obtenha as 10 primeiras observações.</span><span class="sxs-lookup"><span data-stu-id="51052-310">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="51052-311">Itere e gere os rótulos original e previsto para as previsões.</span><span class="sxs-lookup"><span data-stu-id="51052-311">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87-L91)]

1. <span data-ttu-id="51052-312">Por fim, dentro do método `Main`, chame `ClassifyImages` usando o conjunto de teste de imagens.</span><span class="sxs-lookup"><span data-stu-id="51052-312">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

## <a name="run-the-application"></a><span data-ttu-id="51052-313">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="51052-313">Run the application</span></span>

<span data-ttu-id="51052-314">Execute o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="51052-314">Run your console app.</span></span> <span data-ttu-id="51052-315">A saída deve ser semelhante à mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="51052-315">The output should be similar to that below.</span></span> <span data-ttu-id="51052-316">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="51052-316">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="51052-317">Para resumir, a saída foi condensada.</span><span class="sxs-lookup"><span data-stu-id="51052-317">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="51052-318">**Fase de afunilamento**</span><span class="sxs-lookup"><span data-stu-id="51052-318">**Bottleneck phase**</span></span>

<span data-ttu-id="51052-319">Nenhum valor é impresso para o nome da imagem porque as imagens são carregadas como um `byte[]`, portanto, não há nenhum nome de imagem a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="51052-319">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279, Image Name:
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1, Image Name:
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2, Image Name:
```

<span data-ttu-id="51052-320">**Fase de treinamento**</span><span class="sxs-lookup"><span data-stu-id="51052-320">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="51052-321">**Classificar saída de imagens**</span><span class="sxs-lookup"><span data-stu-id="51052-321">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="51052-322">Após a inspeção da imagem *7001 -220. jpg* , você pode ver que, na verdade, ela não está quebrada.</span><span class="sxs-lookup"><span data-stu-id="51052-322">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span> 

![Imagem do conjunto de SDNET2018 usado para previsão](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="51052-324">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="51052-324">Congratulations!</span></span> <span data-ttu-id="51052-325">Agora você criou com êxito um modelo de aprendizado profundo para classificar imagens.</span><span class="sxs-lookup"><span data-stu-id="51052-325">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="51052-326">Melhorar o modelo</span><span class="sxs-lookup"><span data-stu-id="51052-326">Improve the model</span></span>

<span data-ttu-id="51052-327">Se você não estiver satisfeito com os resultados do modelo, poderá tentar melhorar seu desempenho experimentando algumas das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="51052-327">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="51052-328">**Mais dados**: quanto mais exemplos um modelo aprende, melhor é o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51052-328">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="51052-329">Baixe o [conjunto de SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) completo e use-o para treinar.</span><span class="sxs-lookup"><span data-stu-id="51052-329">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span> 
- <span data-ttu-id="51052-330">**Aumentar os dados**: uma técnica comum para adicionar uma variedade aos dados é aumentar os dados, tirando uma imagem e aplicando transformações diferentes (girar, virar, deslocar, cortar).</span><span class="sxs-lookup"><span data-stu-id="51052-330">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="51052-331">Isso adiciona exemplos mais variados para o modelo a ser aprendedo.</span><span class="sxs-lookup"><span data-stu-id="51052-331">This adds more varied examples for the model to learn from.</span></span> 
- <span data-ttu-id="51052-332">**Treine por mais tempo**: quanto mais longo for o treinamento, mais ajustado será o modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-332">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="51052-333">Aumentar o número de épocas pode melhorar o desempenho do seu modelo.</span><span class="sxs-lookup"><span data-stu-id="51052-333">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="51052-334">**Experimente os hiperparâmetros**: além dos parâmetros usados neste tutorial, outros parâmetros podem ser ajustados para melhorar potencialmente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51052-334">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="51052-335">Alterar a taxa de aprendizado, que determina a magnitude das atualizações feitas ao modelo depois que cada época pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="51052-335">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="51052-336">**Use uma arquitetura de modelo diferente**: dependendo de como seus dados se parecem, o modelo que pode aprender melhor seus recursos pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="51052-336">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="51052-337">Se você não estiver satisfeito com o desempenho do seu modelo, tente alterar a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="51052-337">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="51052-338">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="51052-338">Additional Resources</span></span>

- <span data-ttu-id="51052-339">[Aprendizado profundo versus Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="51052-339">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="51052-340">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="51052-340">Next steps</span></span>

<span data-ttu-id="51052-341">Neste tutorial, você aprendeu a criar um modelo de aprendizado profundo personalizado usando o aprendizado de transferência, um modelo TensorFlow de classificação de imagem previamente treinado e a API de classificação de imagem ML.NET para classificar imagens de superfícies concretas como rachadas ou sem cracking.</span><span class="sxs-lookup"><span data-stu-id="51052-341">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="51052-342">Avance para o próximo tutorial para saber mais.</span><span class="sxs-lookup"><span data-stu-id="51052-342">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51052-343">Detecção de objeto</span><span class="sxs-lookup"><span data-stu-id="51052-343">Object Detection</span></span>](object-detection-onnx.md)
