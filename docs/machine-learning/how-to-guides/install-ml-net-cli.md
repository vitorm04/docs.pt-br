---
title: Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET
description: Saiba como instalar, atualizar, fazer downgrade e desinstalar a ferramenta CLI (Command-Line Interface, interface de linha de comando) ML.NET.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848633"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="65237-103">Como instalar a ferramenta da CLI (Interface de Linha de Comando) do ML.NET</span><span class="sxs-lookup"><span data-stu-id="65237-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="65237-104">Saiba como instalar o ML.NET CLI (interface de linha de comando) no Windows, Mac ou Linux.</span><span class="sxs-lookup"><span data-stu-id="65237-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="65237-105">O ML.NET CLI gera boa qualidade ML.NET modelos e código-fonte usando aprendizado automático de máquina (AutoML) e um conjunto de dados de treinamento.</span><span class="sxs-lookup"><span data-stu-id="65237-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="65237-106">Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.</span><span class="sxs-lookup"><span data-stu-id="65237-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="65237-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="65237-107">Pre-requisites</span></span>

- [<span data-ttu-id="65237-108">SDK do .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="65237-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="65237-109">(Opcional) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="65237-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="65237-110">Você pode executar os projetos de código C# gerados com o Visual Studio pressionando a `F5` tecla ou com `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="65237-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="65237-111">Nota: Se depois de instalar [o .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) o `dotnet tool` comando não estiver funcionando, faça login no Windows e faça login novamente.</span><span class="sxs-lookup"><span data-stu-id="65237-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="65237-112">Instalar</span><span class="sxs-lookup"><span data-stu-id="65237-112">Install</span></span>

<span data-ttu-id="65237-113">A CLI do ML.NET é instalada como qualquer outra Ferramenta Global do dotnet.</span><span class="sxs-lookup"><span data-stu-id="65237-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="65237-114">Você usa o comando da CLI do .NET Core `dotnet tool install`.</span><span class="sxs-lookup"><span data-stu-id="65237-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="65237-115">O exemplo a seguir mostra como instalar a CLI do ML.NET no local de feed do NuGet padrão:</span><span class="sxs-lookup"><span data-stu-id="65237-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="65237-116">Se a ferramenta não puder ser instalada (ou seja, não estiver disponível no feed do NuGet padrão), mensagens de erro serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="65237-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="65237-117">Verifique se os feeds esperados estão sendo verificados.</span><span class="sxs-lookup"><span data-stu-id="65237-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="65237-118">Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="65237-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="65237-119">Você pode confirmar que a instalação foi bem-sucedida digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="65237-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="65237-120">Você deve ver a ajuda para os comandos disponíveis para a ferramenta mlnet como o comando 'auto-train'.</span><span class="sxs-lookup"><span data-stu-id="65237-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="65237-121">Instalar uma versão de liberação específica</span><span class="sxs-lookup"><span data-stu-id="65237-121">Install a specific release version</span></span>

<span data-ttu-id="65237-122">Se estiver tentando instalar uma versão de pré-lançamento ou uma versão específica da ferramenta, especifique a [estrutura](../../standard/frameworks.md) usando o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="65237-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="65237-123">Você também poderá verificar se o pacote está instalado corretamente digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="65237-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="65237-124">Desinstalar o pacote da CLI</span><span class="sxs-lookup"><span data-stu-id="65237-124">Uninstall the CLI package</span></span>

<span data-ttu-id="65237-125">Digite o seguinte comando para desinstalar o pacote do seu computador local:</span><span class="sxs-lookup"><span data-stu-id="65237-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="65237-126">Atualizar o pacote da CLI</span><span class="sxs-lookup"><span data-stu-id="65237-126">Update the CLI package</span></span>

<span data-ttu-id="65237-127">Digite o seguinte comando para atualizar o pacote do seu computador local:</span><span class="sxs-lookup"><span data-stu-id="65237-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="65237-128">Configurar sugestões da CLI (preenchimento automático baseado em guia)</span><span class="sxs-lookup"><span data-stu-id="65237-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="65237-129">Como a CLI do ML.NET baseia-se em `System.CommandLine`, ela tem suporte interno para o preenchimento de guia.</span><span class="sxs-lookup"><span data-stu-id="65237-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="65237-130">Um exemplo de como o preenchimento automático de guia funciona é mostrado na animação a seguir:</span><span class="sxs-lookup"><span data-stu-id="65237-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="65237-132">O "preenchimento automático baseado em guia" (sugestões de parâmetro) funciona em *Windows PowerShell* e *bash do macOS/Linux*, mas não funciona no *CMD do Windows*.</span><span class="sxs-lookup"><span data-stu-id="65237-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="65237-133">Para habilitá-lo, na versão prévia atual, o usuário final deve executar algumas etapas uma vez por shell, descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="65237-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="65237-134">Depois que isso for feito, os preenchimentos vão funcionar para todos os aplicativos escritos usando `System.CommandLine`, como a CLI do ML.NET.</span><span class="sxs-lookup"><span data-stu-id="65237-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="65237-135">No computador em que você deseja habilitar o preenchimento, você precisará fazer duas coisas.</span><span class="sxs-lookup"><span data-stu-id="65237-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="65237-136">Instalar a ferramenta global `dotnet-suggest` executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="65237-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="65237-137">Adicionar o script de shim apropriado ao seu perfil de shell.</span><span class="sxs-lookup"><span data-stu-id="65237-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="65237-138">Talvez você precise criar um arquivo de perfil de shell.</span><span class="sxs-lookup"><span data-stu-id="65237-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="65237-139">O script de shim vai encaminhar solicitações de conclusão do seu shell para a ferramenta `dotnet-suggest`, que delega ao aplicativo baseado em `System.CommandLine` apropriado.</span><span class="sxs-lookup"><span data-stu-id="65237-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="65237-140">Para o bash, adicione o conteúdo de [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) a `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="65237-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="65237-141">Para o PowerShell, adicione o conteúdo do [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) a seu perfil do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65237-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="65237-142">Você pode encontrar o caminho esperado para seu perfil do PowerShell executando o comando a seguir em seu console:</span><span class="sxs-lookup"><span data-stu-id="65237-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="65237-143">(Para outros shells, [procure](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) ou abra um [problema](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="65237-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="65237-144">Diretório de instalação</span><span class="sxs-lookup"><span data-stu-id="65237-144">Installation directory</span></span>

<span data-ttu-id="65237-145">A CLI do ML.NET pode ser instalada no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="65237-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="65237-146">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="65237-146">The default directories are:</span></span>

| <span data-ttu-id="65237-147">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="65237-147">OS</span></span>          | <span data-ttu-id="65237-148">Caminho</span><span class="sxs-lookup"><span data-stu-id="65237-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="65237-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="65237-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="65237-150">Windows</span><span class="sxs-lookup"><span data-stu-id="65237-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="65237-151">Esses locais são adicionados ao caminho do usuário quando o SDK é executado pela primeira vez e, portanto, as Ferramentas Globais instaladas nesses locais podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="65237-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="65237-152">Observação: as Ferramentas Globais são específicas ao usuário e não globais no computador.</span><span class="sxs-lookup"><span data-stu-id="65237-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="65237-153">Ser específico ao usuário significa que não é possível instalar uma Ferramenta Global que esteja disponível para todos os usuários do computador.</span><span class="sxs-lookup"><span data-stu-id="65237-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="65237-154">A ferramenta só fica disponível para cada perfil de usuário no qual a ferramenta foi instalada.</span><span class="sxs-lookup"><span data-stu-id="65237-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="65237-155">As Ferramentas Globais também podem ser instaladas em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="65237-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="65237-156">Quando elas forem instaladas em um diretório específico, o usuário precisará garantir que o comando esteja disponível, incluindo o diretório no caminho, chamando o comando com o diretório especificado ou chamando a ferramenta no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="65237-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="65237-157">Nesse caso, a CLI do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="65237-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="65237-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="65237-158">See also</span></span>

- [<span data-ttu-id="65237-159">ML.NET visão geral da CLI</span><span class="sxs-lookup"><span data-stu-id="65237-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="65237-160">Tutorial: Analise o sentimento com o ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="65237-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="65237-161">Guia de referência de comando auto-train da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="65237-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="65237-162">Telemetria na CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="65237-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
