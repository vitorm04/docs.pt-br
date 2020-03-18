---
title: 'Tutorial: Instale e use uma ferramenta global .NET Core'
description: Aprenda a instalar e usar uma ferramenta .NET como ferramenta global.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156732"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="e7bdc-103">Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e7bdc-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="e7bdc-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e7bdc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="e7bdc-105">Este tutorial ensina como instalar e usar uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="e7bdc-106">Você usa uma ferramenta que você cria no [primeiro tutorial desta série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="e7bdc-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7bdc-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e7bdc-107">Prerequisites</span></span>

* <span data-ttu-id="e7bdc-108">Complete o [primeiro tutorial desta série.](global-tools-how-to-create.md)</span><span class="sxs-lookup"><span data-stu-id="e7bdc-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="e7bdc-109">Use a ferramenta como uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="e7bdc-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="e7bdc-110">Instale a ferramenta do pacote executando o comando de instalação da [ferramenta dotnet](dotnet-tool-install.md) na pasta de projeto *microsoft.botsay:*</span><span class="sxs-lookup"><span data-stu-id="e7bdc-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e7bdc-111">O `--global` parâmetro informa ao .NET Core CLI para instalar os binários da ferramenta em um local padrão que é adicionado automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="e7bdc-112">O `--add-source` parâmetro informa ao .NET Core CLI que use temporariamente o diretório *./nupkg* como um feed de origem adicional para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="e7bdc-113">Você deu ao seu pacote um nome exclusivo para ter certeza de que ele só será encontrado no diretório *./nupkg,* não no site Nuget.org.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="e7bdc-114">A saída mostra o comando usado para chamar a ferramenta e a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="e7bdc-115">Invoque a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="e7bdc-116">Se este comando falhar, talvez seja necessário abrir um novo terminal para atualizar o PATH.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="e7bdc-117">Remova a ferramenta executando o comando [de saque da ferramenta dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="e7bdc-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="e7bdc-118">Use a ferramenta como uma ferramenta global instalada em um local personalizado</span><span class="sxs-lookup"><span data-stu-id="e7bdc-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="e7bdc-119">Instale a ferramenta a partir do pacote.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-119">Install the tool from the package.</span></span>

   <span data-ttu-id="e7bdc-120">No Windows:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e7bdc-121">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e7bdc-122">O `--tool-path` parâmetro informa ao .NET Core CLI para instalar os binários da ferramenta no local especificado.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="e7bdc-123">Se o diretório não existe, ele é criado.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="e7bdc-124">Este diretório não é adicionado automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="e7bdc-125">A saída mostra o comando usado para chamar a ferramenta e a versão instalada:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="e7bdc-126">Invoque a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-126">Invoke the tool:</span></span>

   <span data-ttu-id="e7bdc-127">No Windows:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="e7bdc-128">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="e7bdc-129">Remova a ferramenta executando o comando [de saque da ferramenta dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="e7bdc-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="e7bdc-130">No Windows:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="e7bdc-131">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="e7bdc-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="e7bdc-132">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="e7bdc-132">Troubleshoot</span></span>

<span data-ttu-id="e7bdc-133">Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="e7bdc-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7bdc-134">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e7bdc-134">Next steps</span></span>

<span data-ttu-id="e7bdc-135">Neste tutorial, você instalou e usou uma ferramenta como ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="e7bdc-136">Para instalar e usar a mesma ferramenta de uma ferramenta local, avance para o próximo tutorial.</span><span class="sxs-lookup"><span data-stu-id="e7bdc-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7bdc-137">Instale e use ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="e7bdc-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
