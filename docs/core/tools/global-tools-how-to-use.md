---
title: 'Tutorial: instalar e usar uma ferramenta global do .NET Core'
description: Saiba como instalar e usar uma ferramenta .NET como uma ferramenta global.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543869"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="5f8b7-103">Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f8b7-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="5f8b7-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5f8b7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="5f8b7-105">Este tutorial ensina como instalar e usar uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="5f8b7-106">Você usa uma ferramenta que você cria no [primeiro tutorial desta série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b7-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f8b7-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5f8b7-107">Prerequisites</span></span>

* <span data-ttu-id="5f8b7-108">Conclua o [primeiro tutorial desta série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b7-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="5f8b7-109">Usar a ferramenta como uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="5f8b7-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="5f8b7-110">Instale a ferramenta a partir do pacote executando o comando [dotnet ferramenta de instalação](dotnet-tool-install.md) no *nome botsay-\<>* pasta do projeto:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *botsay-\<name>* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="5f8b7-111">O parâmetro `--global` informa ao CLI do .NET Core para instalar os binários da ferramenta em um local padrão que é adicionado automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="5f8b7-112">O parâmetro `--add-source` informa ao CLI do .NET Core para usar temporariamente o diretório *./nupkg* como um feed de origem adicional para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="5f8b7-113">Você deu ao seu pacote um nome exclusivo para certificar-se de que ele só será encontrado no diretório *./nupkg* , não no site do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span> 

   <span data-ttu-id="5f8b7-114">A saída mostra o comando usado para chamar a ferramenta e a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="5f8b7-115">Invoque a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="5f8b7-116">Se esse comando falhar, talvez seja necessário abrir um novo terminal para atualizar o caminho.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="5f8b7-117">Remova a ferramenta executando o comando [dotnet ferramenta de desinstalação](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="5f8b7-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="5f8b7-118">Usar a ferramenta como uma ferramenta global instalada em um local personalizado</span><span class="sxs-lookup"><span data-stu-id="5f8b7-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="5f8b7-119">Instale a ferramenta do pacote.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-119">Install the tool from the package.</span></span>

   <span data-ttu-id="5f8b7-120">No Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="5f8b7-121">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="5f8b7-122">O parâmetro `--tool-path` informa ao CLI do .NET Core para instalar os binários da ferramenta no local especificado.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="5f8b7-123">Se o diretório não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="5f8b7-124">Esse diretório não é adicionado automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="5f8b7-125">A saída mostra o comando usado para chamar a ferramenta e a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="5f8b7-126">Invoque a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-126">Invoke the tool:</span></span>

   <span data-ttu-id="5f8b7-127">No Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="5f8b7-128">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="5f8b7-129">Remova a ferramenta executando o comando [dotnet ferramenta de desinstalação](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="5f8b7-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="5f8b7-130">No Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="5f8b7-131">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="5f8b7-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a><span data-ttu-id="5f8b7-132">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="5f8b7-132">Troubleshoot</span></span>

<span data-ttu-id="5f8b7-133">Se você receber uma mensagem de erro ao seguir o tutorial, consulte [solucionar problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b7-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5f8b7-134">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5f8b7-134">Next steps</span></span>

<span data-ttu-id="5f8b7-135">Neste tutorial, você instalou e usou uma ferramenta como uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="5f8b7-136">Para instalar e usar a mesma ferramenta como uma ferramenta local, avance para o próximo tutorial.</span><span class="sxs-lookup"><span data-stu-id="5f8b7-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f8b7-137">Instalar e usar ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="5f8b7-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
