---
title: Como instalar o suporte de GPU no construtor de modelos
description: Saiba como instalar o suporte a GPU no construtor de modelos
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608561"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="e5ac6-103">Como instalar o suporte de GPU no construtor de modelos</span><span class="sxs-lookup"><span data-stu-id="e5ac6-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="e5ac6-104">Saiba como instalar os drivers de GPU para usar sua GPU com o construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5ac6-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e5ac6-105">Prerequisites</span></span>

- <span data-ttu-id="e5ac6-106">Extensão do Visual Studio do construtor de modelos.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="e5ac6-107">A extensão é incorporada ao Visual Studio a partir da versão 16.6.1.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="e5ac6-108">[Extensão de suporte do Visual Studio GPU do construtor de modelos](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span><span class="sxs-lookup"><span data-stu-id="e5ac6-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="e5ac6-109">Pelo menos uma GPU compatível com CUDA.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="e5ac6-110">Para obter uma lista de GPUs compatíveis, consulte o [Guia do NVIDIA](https://developer.nvidia.com/cuda-gpus).</span><span class="sxs-lookup"><span data-stu-id="e5ac6-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="e5ac6-111">Conta de desenvolvedor NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-111">NVIDIA developer account.</span></span> <span data-ttu-id="e5ac6-112">Se você não tiver uma, [crie uma conta gratuita](https://developer.nvidia.com/developer-program).</span><span class="sxs-lookup"><span data-stu-id="e5ac6-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="e5ac6-113">Instalar dependências</span><span class="sxs-lookup"><span data-stu-id="e5ac6-113">Install dependencies</span></span>

1. <span data-ttu-id="e5ac6-114">Instale o [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span><span class="sxs-lookup"><span data-stu-id="e5ac6-114">Install [CUDA v10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span></span> <span data-ttu-id="e5ac6-115">Certifique-se de instalar o CUDA v 10.0, e não qualquer outra versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-115">Make sure you install CUDA v10.0, not any other newer version.</span></span> <span data-ttu-id="e5ac6-116">Você não pode ter várias versões do CUDA instaladas.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="e5ac6-117">Instale o [cuDNN v 7.6.4 para CUDA 10,0](https://developer.nvidia.com/rdp/cudnn-download).</span><span class="sxs-lookup"><span data-stu-id="e5ac6-117">Install [cuDNN v7.6.4 for CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="e5ac6-118">Você não pode ter várias versões do cuDNN instaladas.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="e5ac6-119">Depois de baixar o arquivo zip cuDNN v 7.6.4 e descompactá-lo, copie `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` para `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .</span><span class="sxs-lookup"><span data-stu-id="e5ac6-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e5ac6-120">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="e5ac6-120">Troubleshooting</span></span>

<span data-ttu-id="e5ac6-121">**Como fazer saber qual GPU eu tenho?**</span><span class="sxs-lookup"><span data-stu-id="e5ac6-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="e5ac6-122">Siga as instruções fornecidas:</span><span class="sxs-lookup"><span data-stu-id="e5ac6-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="e5ac6-123">Clique com o botão direito do mouse em área de trabalho</span><span class="sxs-lookup"><span data-stu-id="e5ac6-123">Right-click on desktop</span></span>
1. <span data-ttu-id="e5ac6-124">Se você vir "painel de controle NVIDIA" ou "vídeo NVIDIA" na janela pop-up, você terá uma GPU NVIDIA</span><span class="sxs-lookup"><span data-stu-id="e5ac6-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="e5ac6-125">Clique em "painel de controle NVIDIA" ou "vídeo NVIDIA" na janela pop-up</span><span class="sxs-lookup"><span data-stu-id="e5ac6-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="e5ac6-126">Veja "informações sobre a placa gráfica"</span><span class="sxs-lookup"><span data-stu-id="e5ac6-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="e5ac6-127">Você verá o nome da GPU NVIDIA</span><span class="sxs-lookup"><span data-stu-id="e5ac6-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="e5ac6-128">**Não vejo o painel de controle NVIDIA (ou ele não é aberto), mas sei que tenho uma GPU NVIDIA.**</span><span class="sxs-lookup"><span data-stu-id="e5ac6-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="e5ac6-129">Abra o Gerenciador de Dispositivos</span><span class="sxs-lookup"><span data-stu-id="e5ac6-129">Open Device Manager</span></span>
1. <span data-ttu-id="e5ac6-130">Examinar adaptadores de vídeo</span><span class="sxs-lookup"><span data-stu-id="e5ac6-130">Look at Display adapters</span></span>
1. <span data-ttu-id="e5ac6-131">Instale o [Driver](https://www.nvidia.com/drivers) apropriado para sua GPU.</span><span class="sxs-lookup"><span data-stu-id="e5ac6-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
