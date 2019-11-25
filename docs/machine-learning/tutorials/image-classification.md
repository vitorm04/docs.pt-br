---
title: 'Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model'
description: Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model. The TensorFlow model was trained to classify images into a thousand categories. The ML.NET model makes use of transfer learning to classify images into fewer broader categories.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 952ce5c52bcd09b8c4e4e40d5ddf85835a26478d
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204996"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="678ad-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span><span class="sxs-lookup"><span data-stu-id="678ad-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="678ad-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span><span class="sxs-lookup"><span data-stu-id="678ad-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="678ad-107">The TensorFlow model was trained to classify images into a thousand categories.</span><span class="sxs-lookup"><span data-stu-id="678ad-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="678ad-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span><span class="sxs-lookup"><span data-stu-id="678ad-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="678ad-109">Treinar um modelo de [Classificação de Imagens](https://en.wikipedia.org/wiki/Outline_of_object_recognition) do zero requer a configuração de milhões de parâmetros, uma tonelada de dados de treinamento rotulados e uma grande quantidade de recursos de computação (centenas de horas de GPU).</span><span class="sxs-lookup"><span data-stu-id="678ad-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="678ad-110">Embora não seja tão eficaz quanto treinar um modelo personalizado do zero, o aprendizado de transferência permite que você ative esse processo trabalhando com milhares de imagens em comparação com milhões de imagens rotuladas e crie um modelo personalizado rapidamente (em uma hora em uma máquina sem GPU).</span><span class="sxs-lookup"><span data-stu-id="678ad-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="678ad-111">This tutorial scales that process down even further, using only a dozen training images.</span><span class="sxs-lookup"><span data-stu-id="678ad-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="678ad-112">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="678ad-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="678ad-113">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="678ad-113">Understand the problem</span></span>
> * <span data-ttu-id="678ad-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="678ad-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="678ad-115">Train and evaluate the ML.NET model</span><span class="sxs-lookup"><span data-stu-id="678ad-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="678ad-116">Classify a test image</span><span class="sxs-lookup"><span data-stu-id="678ad-116">Classify a test image</span></span>

<span data-ttu-id="678ad-117">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="678ad-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="678ad-118">Observe que, por padrão, a configuração de projeto do .NET para este tutorial se destina ao .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="678ad-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="678ad-119">O que é o aprendizado por transferência?</span><span class="sxs-lookup"><span data-stu-id="678ad-119">What is transfer learning?</span></span>

<span data-ttu-id="678ad-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span><span class="sxs-lookup"><span data-stu-id="678ad-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="678ad-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span><span class="sxs-lookup"><span data-stu-id="678ad-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="678ad-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="678ad-122">Prerequisites</span></span>

* <span data-ttu-id="678ad-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span><span class="sxs-lookup"><span data-stu-id="678ad-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
* [<span data-ttu-id="678ad-124">O arquivo .ZIP do diretório de recursos do tutorial</span><span class="sxs-lookup"><span data-stu-id="678ad-124">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [<span data-ttu-id="678ad-125">O modelo de machine learning do InceptionV1</span><span class="sxs-lookup"><span data-stu-id="678ad-125">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="678ad-126">Select the right machine learning task</span><span class="sxs-lookup"><span data-stu-id="678ad-126">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="678ad-127">Aprendizado profundo</span><span class="sxs-lookup"><span data-stu-id="678ad-127">Deep learning</span></span>

<span data-ttu-id="678ad-128">[Aprendizado profundo](https://en.wikipedia.org/wiki/Deep_learning) é um subconjunto do aprendizado de máquina, que está revolucionando áreas como Pesquisa Visual Computacional e Reconhecimento de Fala.</span><span class="sxs-lookup"><span data-stu-id="678ad-128">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="678ad-129">Os modelos de aprendizado profundo são treinados usando grandes conjuntos de [dados rotulados](https://en.wikipedia.org/wiki/Labeled_data) e [redes neurais](https://en.wikipedia.org/wiki/Artificial_neural_network) que contêm várias camadas de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="678ad-129">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="678ad-130">Aprendizado profundo:</span><span class="sxs-lookup"><span data-stu-id="678ad-130">Deep learning:</span></span>

* <span data-ttu-id="678ad-131">Funciona melhor em algumas tarefas como a Pesquisa Visual Computacional.</span><span class="sxs-lookup"><span data-stu-id="678ad-131">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="678ad-132">Requires huge amounts of training data.</span><span class="sxs-lookup"><span data-stu-id="678ad-132">Requires huge amounts of training data.</span></span>

<span data-ttu-id="678ad-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span><span class="sxs-lookup"><span data-stu-id="678ad-133">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="678ad-134">Detectar uma face humana em uma imagem ou não.</span><span class="sxs-lookup"><span data-stu-id="678ad-134">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="678ad-135">Detecting cats vs. dogs.</span><span class="sxs-lookup"><span data-stu-id="678ad-135">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="678ad-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span><span class="sxs-lookup"><span data-stu-id="678ad-136">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="678ad-137">![imagem de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![imagem de ursinho de pelúcia](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![imagem de torradeira](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="678ad-137">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="678ad-138">As imagens anteriores pertencem ao Wikimedia Commons e são atribuídas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="678ad-138">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="678ad-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span><span class="sxs-lookup"><span data-stu-id="678ad-139">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="678ad-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span><span class="sxs-lookup"><span data-stu-id="678ad-140">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="678ad-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span><span class="sxs-lookup"><span data-stu-id="678ad-141">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="678ad-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span><span class="sxs-lookup"><span data-stu-id="678ad-142">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="678ad-143">Digite a parte `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="678ad-143">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="678ad-144">Você pode transferir a capacidade de `Inception model` de reconhecer e classificar imagens para as novas categorias limitadas do seu classificador de imagens personalizadas.</span><span class="sxs-lookup"><span data-stu-id="678ad-144">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="678ad-145">Alimentação</span><span class="sxs-lookup"><span data-stu-id="678ad-145">Food</span></span>
* <span data-ttu-id="678ad-146">Brinquedos</span><span class="sxs-lookup"><span data-stu-id="678ad-146">Toy</span></span>
* <span data-ttu-id="678ad-147">Dispositivos</span><span class="sxs-lookup"><span data-stu-id="678ad-147">Appliance</span></span>

<span data-ttu-id="678ad-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span><span class="sxs-lookup"><span data-stu-id="678ad-148">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="678ad-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span><span class="sxs-lookup"><span data-stu-id="678ad-149">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="678ad-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span><span class="sxs-lookup"><span data-stu-id="678ad-150">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="678ad-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span><span class="sxs-lookup"><span data-stu-id="678ad-151">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="678ad-152">Conforme mostrado no diagrama a seguir, você adiciona uma referência aos pacotes ML.NET NuGet em seus aplicativos .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="678ad-152">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="678ad-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span><span class="sxs-lookup"><span data-stu-id="678ad-153">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagrama de arco da transformação do TensorFlow do ML.NET](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="678ad-155">Classificação multiclasse</span><span class="sxs-lookup"><span data-stu-id="678ad-155">Multiclass classification</span></span>

<span data-ttu-id="678ad-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="678ad-156">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="678ad-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="678ad-157">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="678ad-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span><span class="sxs-lookup"><span data-stu-id="678ad-158">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="678ad-159">Dados</span><span class="sxs-lookup"><span data-stu-id="678ad-159">Data</span></span>

<span data-ttu-id="678ad-160">Há duas fontes de dados: o arquivo `.tsv` e os arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-160">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="678ad-161">O arquivo `tags.tsv` contém duas colunas: a primeira é definida como `ImagePath` e a segunda é a `Label` correspondente à imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-161">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="678ad-162">O arquivo de exemplo a seguir não possui uma linha de cabeçalho e tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="678ad-162">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="678ad-163">As imagens de treinamento e teste estão localizadas nas pastas de recursos que você baixará em um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="678ad-163">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="678ad-164">Essas imagens pertencem ao Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="678ad-164">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="678ad-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), o repositório de mídia gratuito.*</span><span class="sxs-lookup"><span data-stu-id="678ad-165">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="678ad-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="678ad-166">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="678ad-167">Configuração</span><span class="sxs-lookup"><span data-stu-id="678ad-167">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="678ad-168">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="678ad-168">Create a project</span></span>

1. <span data-ttu-id="678ad-169">Criar um **Aplicativo de Console .NET Core** chamado "TransferLearningTF".</span><span class="sxs-lookup"><span data-stu-id="678ad-169">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="678ad-170">Instalar o **Pacote NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="678ad-170">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="678ad-171">No Gerenciador de Soluções, clique com o botão direito do mouse no seu projeto e selecione **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="678ad-171">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="678ad-172">Escolha "nuget.org" como a fonte do pacote, selecione a guia Browse, procure por **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="678ad-172">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="678ad-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span><span class="sxs-lookup"><span data-stu-id="678ad-173">Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="678ad-174">Select the **OK** button on the **Preview Changes** dialog.</span><span class="sxs-lookup"><span data-stu-id="678ad-174">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="678ad-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span><span class="sxs-lookup"><span data-stu-id="678ad-175">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="678ad-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="678ad-176">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="678ad-177">Download assets</span><span class="sxs-lookup"><span data-stu-id="678ad-177">Download assets</span></span>

1. <span data-ttu-id="678ad-178">Baixe o [arquivo zip do diretório de materiais do projeto](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) e descompacte.</span><span class="sxs-lookup"><span data-stu-id="678ad-178">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="678ad-179">Copie o diretório`assets` no diretório do projeto *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="678ad-179">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="678ad-180">Este diretório e seus subdiretórios contêm os arquivos de dados e de suporte (exceto o modelo Concepção, que você irá baixar e adicionar na próxima etapa) necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="678ad-180">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="678ad-181">Baixe o [modelo Concepção](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) e descompacte-o.</span><span class="sxs-lookup"><span data-stu-id="678ad-181">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="678ad-182">Copie o conteúdo do diretório `inception5h` apenas descompactado em seu diretório de projeto *TransferLearningTF*`assets/inception`.</span><span class="sxs-lookup"><span data-stu-id="678ad-182">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="678ad-183">Este diretório contém o modelo e os arquivos de suporte adicionais necessários para este tutorial, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="678ad-183">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Conteúdo do diretório de concepção](./media/image-classification/inception-files.png)

1. <span data-ttu-id="678ad-185">No Gerenciador de Soluções, clique com o botão direito do mouse em cada um dos arquivos no diretório e nos subdiretórios do ativo e selecione**Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="678ad-185">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="678ad-186">Em **Avançado**, altere o valor de **Copiar para Diretório de Saída** para **Copiar se for mais novo**.</span><span class="sxs-lookup"><span data-stu-id="678ad-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="678ad-187">Criar classes e definir demarcadores</span><span class="sxs-lookup"><span data-stu-id="678ad-187">Create classes and define paths</span></span>

1. <span data-ttu-id="678ad-188">Adicione as seguintes instruções `using` adicionais ao início do arquivo *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="678ad-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="678ad-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span><span class="sxs-lookup"><span data-stu-id="678ad-189">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="678ad-190">Create classes for your input data, and predictions.</span><span class="sxs-lookup"><span data-stu-id="678ad-190">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="678ad-191">`ImageData` é a classe de conjunto de dados de entrada e tem os seguintes campos <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="678ad-191">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="678ad-192">`ImagePath` contém o nome do arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-192">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="678ad-193">`Label` contém um valor para o rótulo da imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-193">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="678ad-194">Adicione uma nova classe ao seu projeto para `ImagePrediction`:</span><span class="sxs-lookup"><span data-stu-id="678ad-194">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="678ad-195">`ImagePrediction` é a classe de previsão de imagem e possui os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="678ad-195">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="678ad-196">`Score` contém a porcentagem de confiança para uma determinada classificação de imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-196">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="678ad-197">`PredictedLabelValue` contém um valor para o rótulo de classificação de imagem previsto.</span><span class="sxs-lookup"><span data-stu-id="678ad-197">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="678ad-198">`ImagePrediction` é a classe usada para previsão depois que o modelo foi treinado.</span><span class="sxs-lookup"><span data-stu-id="678ad-198">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="678ad-199">Tem um `string` (`ImagePath`) para o demarcador da imagem.</span><span class="sxs-lookup"><span data-stu-id="678ad-199">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="678ad-200">The `Label` is used to reuse and train the model.</span><span class="sxs-lookup"><span data-stu-id="678ad-200">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="678ad-201">O `PredictedLabelValue` é usado durante a previsão e avaliação.</span><span class="sxs-lookup"><span data-stu-id="678ad-201">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="678ad-202">Para avaliação, uma entrada com dados de treinamento, os valores previstos e o modelo são usados.</span><span class="sxs-lookup"><span data-stu-id="678ad-202">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="678ad-203">Inicializar variáveis em Main</span><span class="sxs-lookup"><span data-stu-id="678ad-203">Initialize variables in Main</span></span>

1. <span data-ttu-id="678ad-204">Inicialize a variável `mlContext` com uma nova instância de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="678ad-204">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="678ad-205">Substitua a linha `Console.WriteLine("Hello World!")` pelo seguinte código no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="678ad-205">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="678ad-206">A [classe MLContext](xref:Microsoft.ML.MLContext) é um ponto de partida para todas as operações do ML.NET e a inicialização do `mlContext` cria um ambiente do ML.NET que pode ser compartilhado entre os objetos de fluxo de trabalho da criação de modelo.</span><span class="sxs-lookup"><span data-stu-id="678ad-206">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="678ad-207">Ele é semelhante, conceitualmente, a `DBContext` no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="678ad-207">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="678ad-208">Create a struct for Inception model parameters</span><span class="sxs-lookup"><span data-stu-id="678ad-208">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="678ad-209">The Inception model has several parameters you need to pass in.</span><span class="sxs-lookup"><span data-stu-id="678ad-209">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="678ad-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-210">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="678ad-211">Criar um método de utilitário de exibição</span><span class="sxs-lookup"><span data-stu-id="678ad-211">Create a display utility method</span></span>

<span data-ttu-id="678ad-212">Uma vez que você exibirá os dados de imagem e as previsões relacionadas mais de uma vez, crie um método de utilitário de exibição para lidar com a exibição dos resultados de imagem e previsão.</span><span class="sxs-lookup"><span data-stu-id="678ad-212">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="678ad-213">Crie o método `DisplayResults()`, logo após o struct `InceptionSettings`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="678ad-213">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="678ad-214">Fill in the body of the `DisplayResults` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-214">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="678ad-215">Criar um método de utilitário de arquivo .tsv</span><span class="sxs-lookup"><span data-stu-id="678ad-215">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="678ad-216">Crie o método `ReadFromTsv()`, logo após o método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="678ad-216">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="678ad-217">Fill in the body of the `ReadFromTsv` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-217">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="678ad-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span><span class="sxs-lookup"><span data-stu-id="678ad-218">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="678ad-219">Create a method to make a prediction</span><span class="sxs-lookup"><span data-stu-id="678ad-219">Create a method to make a prediction</span></span>

1. <span data-ttu-id="678ad-220">Crie o método `ClassifySingleImage()`, logo antes do método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="678ad-220">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="678ad-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="678ad-221">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="678ad-222">Adicione o seguinte código como as próximas linhas no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="678ad-222">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="678ad-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-223">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="678ad-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span><span class="sxs-lookup"><span data-stu-id="678ad-224">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="678ad-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="678ad-225">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="678ad-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) não é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="678ad-226">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="678ad-227">It's acceptable to use in single-threaded or prototype environments.</span><span class="sxs-lookup"><span data-stu-id="678ad-227">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="678ad-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span><span class="sxs-lookup"><span data-stu-id="678ad-228">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="678ad-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="678ad-229">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="678ad-230">A extensão de serviço `PredictionEnginePool` está atualmente em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="678ad-230">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="678ad-231">Exiba o resultado da previsão como a próxima linha de código no método `ClassifySingleImage()`:</span><span class="sxs-lookup"><span data-stu-id="678ad-231">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="678ad-232">Construct the ML.NET model pipeline</span><span class="sxs-lookup"><span data-stu-id="678ad-232">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="678ad-233">An ML.NET model pipeline is a chain of estimators.</span><span class="sxs-lookup"><span data-stu-id="678ad-233">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="678ad-234">Note that no execution happens during pipeline construction.</span><span class="sxs-lookup"><span data-stu-id="678ad-234">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="678ad-235">The estimator objects are created but not executed.</span><span class="sxs-lookup"><span data-stu-id="678ad-235">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="678ad-236">Add a method to generate the model</span><span class="sxs-lookup"><span data-stu-id="678ad-236">Add a method to generate the model</span></span>

    <span data-ttu-id="678ad-237">This method is the heart of the tutorial.</span><span class="sxs-lookup"><span data-stu-id="678ad-237">This method is the heart of the tutorial.</span></span> <span data-ttu-id="678ad-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span><span class="sxs-lookup"><span data-stu-id="678ad-238">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="678ad-239">It also evaluates the model against some previously unseen test data.</span><span class="sxs-lookup"><span data-stu-id="678ad-239">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="678ad-240">Crie o método `GenerateModel()` logo após o struct `InceptionSettings` e antes do método `DisplayResults()`, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="678ad-240">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="678ad-241">Add the estimators to load, resize and extract the pixels from the image data:</span><span class="sxs-lookup"><span data-stu-id="678ad-241">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="678ad-242">The image data needs to be processed into the format that the TensorFlow model expects.</span><span class="sxs-lookup"><span data-stu-id="678ad-242">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="678ad-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span><span class="sxs-lookup"><span data-stu-id="678ad-243">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="678ad-244">Add the estimator to load the TensorFlow model, and score it:</span><span class="sxs-lookup"><span data-stu-id="678ad-244">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="678ad-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span><span class="sxs-lookup"><span data-stu-id="678ad-245">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="678ad-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span><span class="sxs-lookup"><span data-stu-id="678ad-246">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="678ad-247">When using the model in its entirety, scoring makes an inference, or prediction.</span><span class="sxs-lookup"><span data-stu-id="678ad-247">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="678ad-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span><span class="sxs-lookup"><span data-stu-id="678ad-248">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="678ad-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="678ad-249">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="678ad-250">The output of this layer is effectively a vector of features that characterize the original input images.</span><span class="sxs-lookup"><span data-stu-id="678ad-250">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="678ad-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span><span class="sxs-lookup"><span data-stu-id="678ad-251">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="678ad-252">Add the estimator to map the string labels in the training data to integer key values:</span><span class="sxs-lookup"><span data-stu-id="678ad-252">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="678ad-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span><span class="sxs-lookup"><span data-stu-id="678ad-253">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="678ad-254">A key is a number that has a one to one mapping to a string value.</span><span class="sxs-lookup"><span data-stu-id="678ad-254">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="678ad-255">Add the ML.NET training algorithm:</span><span class="sxs-lookup"><span data-stu-id="678ad-255">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="678ad-256">Add the estimator to map the predicted key value back into a string:</span><span class="sxs-lookup"><span data-stu-id="678ad-256">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="678ad-257">Treinar o modelo</span><span class="sxs-lookup"><span data-stu-id="678ad-257">Train the model</span></span>

1. <span data-ttu-id="678ad-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span><span class="sxs-lookup"><span data-stu-id="678ad-258">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="678ad-259">Adicione o seguinte código ao método `GenerateModel()` como a linha seguinte:</span><span class="sxs-lookup"><span data-stu-id="678ad-259">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="678ad-260">Os dados do ML.NET são representados como uma [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="678ad-260">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="678ad-261">`IDataView` é uma maneira flexível e eficiente de descrever dados tabulares (numéricos e texto).</span><span class="sxs-lookup"><span data-stu-id="678ad-261">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="678ad-262">Os dados podem ser carregados de um arquivo de texto ou em tempo real (por exemplo, banco de dados SQL ou arquivos de log) para um objeto `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="678ad-262">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="678ad-263">Train the model with the data loaded above:</span><span class="sxs-lookup"><span data-stu-id="678ad-263">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="678ad-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span><span class="sxs-lookup"><span data-stu-id="678ad-264">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="678ad-265">Evaluate the accuracy of the model</span><span class="sxs-lookup"><span data-stu-id="678ad-265">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="678ad-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-266">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="678ad-267">There are a few sample images that you can use to evaluate the model.</span><span class="sxs-lookup"><span data-stu-id="678ad-267">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="678ad-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span><span class="sxs-lookup"><span data-stu-id="678ad-268">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="678ad-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span><span class="sxs-lookup"><span data-stu-id="678ad-269">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="678ad-270">Depois de determinar a previsão, o método [Evaluate ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A):</span><span class="sxs-lookup"><span data-stu-id="678ad-270">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="678ad-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span><span class="sxs-lookup"><span data-stu-id="678ad-271">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="678ad-272">Retorna as métricas de desempenho do modelo.</span><span class="sxs-lookup"><span data-stu-id="678ad-272">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="678ad-273">Display the model accuracy metrics</span><span class="sxs-lookup"><span data-stu-id="678ad-273">Display the model accuracy metrics</span></span>

    <span data-ttu-id="678ad-274">Use o código a seguir para exibir as métricas, compartilhar os resultados e, em seguida, agir com relação a eles:</span><span class="sxs-lookup"><span data-stu-id="678ad-274">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="678ad-275">As seguintes métricas são avaliadas para classificação de imagem:</span><span class="sxs-lookup"><span data-stu-id="678ad-275">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="678ad-276">`Log-loss` - confira [Perda de log](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="678ad-276">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="678ad-277">Convém que a Perda de log seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="678ad-277">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="678ad-278">`Per class Log-loss`</span><span class="sxs-lookup"><span data-stu-id="678ad-278">`Per class Log-loss`.</span></span> <span data-ttu-id="678ad-279">Convém que a Perda de log por classe seja tão próxima de zero quanto possível.</span><span class="sxs-lookup"><span data-stu-id="678ad-279">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="678ad-280">Adicione o seguinte código para retornar o modelo treinado como a próxima linha:</span><span class="sxs-lookup"><span data-stu-id="678ad-280">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="678ad-281">Run the application!</span><span class="sxs-lookup"><span data-stu-id="678ad-281">Run the application!</span></span>

1. <span data-ttu-id="678ad-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span><span class="sxs-lookup"><span data-stu-id="678ad-282">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="678ad-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span><span class="sxs-lookup"><span data-stu-id="678ad-283">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="678ad-284">Run your console app (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="678ad-284">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="678ad-285">O resultado deverá ser semelhante à seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="678ad-285">Your results should be similar to the following output.</span></span>  <span data-ttu-id="678ad-286">Você poderá ver avisos ou mensagens de processamento, mas essas mensagens foram removidas dos resultados a seguir para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="678ad-286">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="678ad-287">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="678ad-287">Congratulations!</span></span> <span data-ttu-id="678ad-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span><span class="sxs-lookup"><span data-stu-id="678ad-288">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="678ad-289">Você pode encontrar o código-fonte para este tutorial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="678ad-289">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="678ad-290">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="678ad-290">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="678ad-291">Compreender o problema</span><span class="sxs-lookup"><span data-stu-id="678ad-291">Understand the problem</span></span>
> * <span data-ttu-id="678ad-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span><span class="sxs-lookup"><span data-stu-id="678ad-292">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="678ad-293">Train and evaluate the ML.NET model</span><span class="sxs-lookup"><span data-stu-id="678ad-293">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="678ad-294">Classify a test image</span><span class="sxs-lookup"><span data-stu-id="678ad-294">Classify a test image</span></span>

<span data-ttu-id="678ad-295">Conferir o repositório GitHub de Amostras de Aprendizado de Máquina para explorar uma amostra de classificação de imagem expandida.</span><span class="sxs-lookup"><span data-stu-id="678ad-295">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="678ad-296">dotnet/machinelearning-samples GitHub repository</span><span class="sxs-lookup"><span data-stu-id="678ad-296">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
