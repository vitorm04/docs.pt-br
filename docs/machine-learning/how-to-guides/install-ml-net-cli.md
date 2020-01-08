---
title: Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET
description: Saiba como instalar, atualizar, fazer downgrade e desinstalar a ferramenta de interface de linha de comando (CLI) do ML.NET.
ms.date: 12/18/2019
ms.author: nakersha
author: natke
ms.openlocfilehash: 07b6e924ed9c6b0c278a86539ebe7d750f9ced37
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636582"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="02804-103">Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET</span><span class="sxs-lookup"><span data-stu-id="02804-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="02804-104">Saiba como instalar a CLI do ML.NET (interface de linha de comando) no Windows, Mac ou Linux.</span><span class="sxs-lookup"><span data-stu-id="02804-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="02804-105">A CLI do ML.NET gera bons modelos de ML.NET de qualidade e código-fonte usando o AutoML (Machine Learning automatizado) e um conjunto de informações de treinamento.</span><span class="sxs-lookup"><span data-stu-id="02804-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="02804-106">Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="02804-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="02804-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="02804-107">Pre-requisites</span></span>

- [<span data-ttu-id="02804-108">SDK do .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="02804-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="02804-109">(Opcional) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="02804-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="02804-110">Você pode executar os projetos C# de código gerados com o Visual Studio pressionando a tecla `F5` ou com `dotnet run` (CLI do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="02804-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="02804-111">Observação: se, depois de instalar o [SDK do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) , o comando `dotnet tool` não estiver funcionando, saia do Windows e entre novamente.</span><span class="sxs-lookup"><span data-stu-id="02804-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="02804-112">Instalar o</span><span class="sxs-lookup"><span data-stu-id="02804-112">Install</span></span>

<span data-ttu-id="02804-113">A CLI do ML.NET é instalada como qualquer outra Ferramenta Global do dotnet.</span><span class="sxs-lookup"><span data-stu-id="02804-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="02804-114">Você usa o comando da CLI do .NET Core `dotnet tool install`.</span><span class="sxs-lookup"><span data-stu-id="02804-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="02804-115">O exemplo a seguir mostra como instalar a CLI do ML.NET no local de feed do NuGet padrão:</span><span class="sxs-lookup"><span data-stu-id="02804-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="02804-116">Se a ferramenta não puder ser instalada (ou seja, não estiver disponível no feed do NuGet padrão), mensagens de erro serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="02804-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="02804-117">Verifique se os feeds esperados estão sendo verificados.</span><span class="sxs-lookup"><span data-stu-id="02804-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="02804-118">Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="02804-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="02804-119">Você pode confirmar que a instalação foi bem-sucedida digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02804-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="02804-120">Você deve ver a ajuda para os comandos disponíveis para a ferramenta mlnet como o comando 'auto-train'.</span><span class="sxs-lookup"><span data-stu-id="02804-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="02804-121">Instalar uma versão de liberação específica</span><span class="sxs-lookup"><span data-stu-id="02804-121">Install a specific release version</span></span>

<span data-ttu-id="02804-122">Se estiver tentando instalar uma versão de pré-lançamento ou uma versão específica da ferramenta, especifique a [estrutura](../../standard/frameworks.md) usando o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="02804-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="02804-123">Você também poderá verificar se o pacote está instalado corretamente digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02804-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="02804-124">Desinstalar o pacote da CLI</span><span class="sxs-lookup"><span data-stu-id="02804-124">Uninstall the CLI package</span></span>

<span data-ttu-id="02804-125">Digite o seguinte comando para desinstalar o pacote do seu computador local:</span><span class="sxs-lookup"><span data-stu-id="02804-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="02804-126">Atualizar o pacote da CLI</span><span class="sxs-lookup"><span data-stu-id="02804-126">Update the CLI package</span></span>

<span data-ttu-id="02804-127">Digite o seguinte comando para atualizar o pacote do seu computador local:</span><span class="sxs-lookup"><span data-stu-id="02804-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="02804-128">Configurar sugestões da CLI (preenchimento automático baseado em guia)</span><span class="sxs-lookup"><span data-stu-id="02804-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="02804-129">Como a CLI do ML.NET baseia-se em `System.CommandLine`, ela tem suporte interno para o preenchimento de guia.</span><span class="sxs-lookup"><span data-stu-id="02804-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="02804-130">Um exemplo de como o preenchimento automático de guia funciona é mostrado na animação a seguir:</span><span class="sxs-lookup"><span data-stu-id="02804-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![imagem](./media/cli-tab-completion.gif)

<span data-ttu-id="02804-132">O "preenchimento automático baseado em guia" (sugestões de parâmetro) funciona em *Windows PowerShell* e *bash do macOS/Linux*, mas não funciona no *CMD do Windows*.</span><span class="sxs-lookup"><span data-stu-id="02804-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="02804-133">Para habilitá-lo, na versão prévia atual, o usuário final deve executar algumas etapas uma vez por shell, descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="02804-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="02804-134">Depois que isso for feito, os preenchimentos vão funcionar para todos os aplicativos escritos usando `System.CommandLine`, como a CLI do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="02804-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="02804-135">No computador em que você deseja habilitar o preenchimento, você precisará fazer duas coisas.</span><span class="sxs-lookup"><span data-stu-id="02804-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="02804-136">Instalar a ferramenta global `dotnet-suggest` executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="02804-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="02804-137">Adicionar o script de shim apropriado ao seu perfil de shell.</span><span class="sxs-lookup"><span data-stu-id="02804-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="02804-138">Talvez você precise criar um arquivo de perfil de shell.</span><span class="sxs-lookup"><span data-stu-id="02804-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="02804-139">O script de shim vai encaminhar solicitações de conclusão do seu shell para a ferramenta `dotnet-suggest`, que delega ao aplicativo baseado em `System.CommandLine` apropriado.</span><span class="sxs-lookup"><span data-stu-id="02804-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="02804-140">Para o bash, adicione o conteúdo de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) a `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="02804-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="02804-141">Para o PowerShell, adicione o conteúdo do [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) a seu perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="02804-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="02804-142">Você pode encontrar o caminho esperado para seu perfil do PowerShell executando o comando a seguir em seu console:</span><span class="sxs-lookup"><span data-stu-id="02804-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="02804-143">(Para outros shells, [procure](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou abra um [problema](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="02804-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="02804-144">Diretório de instalação</span><span class="sxs-lookup"><span data-stu-id="02804-144">Installation directory</span></span>

<span data-ttu-id="02804-145">A CLI do ML.NET pode ser instalada no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="02804-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="02804-146">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="02804-146">The default directories are:</span></span>

| <span data-ttu-id="02804-147">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="02804-147">OS</span></span>          | <span data-ttu-id="02804-148">Caminho</span><span class="sxs-lookup"><span data-stu-id="02804-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="02804-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="02804-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="02804-150">Portal</span><span class="sxs-lookup"><span data-stu-id="02804-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="02804-151">Esses locais são adicionados ao caminho do usuário quando o SDK é executado pela primeira vez e, portanto, as Ferramentas Globais instaladas nesses locais podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="02804-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="02804-152">Observação: as Ferramentas Globais são específicas ao usuário e não globais no computador.</span><span class="sxs-lookup"><span data-stu-id="02804-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="02804-153">Ser específico ao usuário significa que não é possível instalar uma Ferramenta Global que esteja disponível para todos os usuários do computador.</span><span class="sxs-lookup"><span data-stu-id="02804-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="02804-154">A ferramenta só fica disponível para cada perfil de usuário no qual a ferramenta foi instalada.</span><span class="sxs-lookup"><span data-stu-id="02804-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="02804-155">As Ferramentas Globais também podem ser instaladas em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="02804-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="02804-156">Quando elas forem instaladas em um diretório específico, o usuário precisará garantir que o comando esteja disponível, incluindo o diretório no caminho, chamando o comando com o diretório especificado ou chamando a ferramenta no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="02804-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="02804-157">Nesse caso, a CLI do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="02804-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="02804-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="02804-158">See also</span></span>

- [<span data-ttu-id="02804-159">Visão geral da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="02804-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="02804-160">Tutorial: analisar o sentimentos com a CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="02804-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="02804-161">Guia de referência de comando auto-train da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="02804-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="02804-162">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="02804-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
