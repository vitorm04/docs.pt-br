---
title: Habilitar o preenchimento com TAB
description: Este artigo ensina você a habilitar o preenchimento com TAB na CLI do .NET Core para o PowerShell, o Bash e o zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 16574e02aa9f9167602401eef2ad7a73e07ad107
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203331"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="e4f7d-103">Como habilitar o preenchimento com TAB para a CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4f7d-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="e4f7d-104">Começando no SDK do .NET Core 2.0, a CLI do .NET Core dá suporte ao preenchimento com TAB.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="e4f7d-105">Este artigo descreve como configurar o preenchimento com TAB para três shells: PowerShell, Bash e zsh.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="e4f7d-106">Outros shells podem ter suporte para preenchimento automático.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="e4f7d-107">Veja a documentação deles para saber como configurar o preenchimento automático. As etapas devem ser semelhantes às etapas descritas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="e4f7d-108">Depois de configurado, o preenchimento com TAB na CLI do .NET Core é disparado pela digitação de um comando `dotnet` no shell e, em seguida, pelo pressionamento da tecla TAB.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="e4f7d-109">A linha de comando atual é enviada para o comando `dotnet complete`, e os resultados são processados pelo shell.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="e4f7d-110">Teste os resultados sem habilitar o preenchimento com TAB enviando algo diretamente para o comando `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="e4f7d-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4f7d-111">For example:</span></span>

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="e4f7d-112">Se esse comando não funcionar, verifique se esse SDK do .NET Core 2.0 ou superior está instalado.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="e4f7d-113">Se ele está instalado, mas esse comando ainda não funciona, verifique se o comando `dotnet` é resolvido para uma versão do SDK do .NET Core 2.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="e4f7d-114">Use o comando `dotnet --version` para ver para qual versão do `dotnet` o caminho atual está sendo resolvido.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="e4f7d-115">Para obter mais informações, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="e4f7d-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="e4f7d-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e4f7d-116">Examples</span></span>

<span data-ttu-id="e4f7d-117">Estes são alguns exemplos do que o preenchimento com TAB fornece:</span><span class="sxs-lookup"><span data-stu-id="e4f7d-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="e4f7d-118">Entrada</span><span class="sxs-lookup"><span data-stu-id="e4f7d-118">Input</span></span>                                | <span data-ttu-id="e4f7d-119">se torna</span><span class="sxs-lookup"><span data-stu-id="e4f7d-119">becomes</span></span>                                                                     | <span data-ttu-id="e4f7d-120">porque</span><span class="sxs-lookup"><span data-stu-id="e4f7d-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="e4f7d-121">`add` é o primeiro subcomando, em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="e4f7d-122">O preenchimento com TAB faz a correspondência de subcadeias de caracteres e `--help` vem em primeiro lugar em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="e4f7d-123">Na segunda vez que a tecla TAB é pressionada, a próxima sugestão é exibida.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="e4f7d-124">Os resultados são retornados em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="e4f7d-125">O preenchimento com TAB reconhece o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="e4f7d-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4f7d-126">PowerShell</span></span>

<span data-ttu-id="e4f7d-127">Para adicionar o preenchimento com TAB ao **PowerShell** na CLI do .NET Core, crie ou edite o perfil armazenado na variável `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="e4f7d-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="e4f7d-128">Para obter mais informações, confira [Como criar seu perfil](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) e [Perfis e política de execução](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="e4f7d-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="e4f7d-129">Adicione o seguinte código ao seu perfil:</span><span class="sxs-lookup"><span data-stu-id="e4f7d-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="e4f7d-130">Bash</span><span class="sxs-lookup"><span data-stu-id="e4f7d-130">Bash</span></span>

<span data-ttu-id="e4f7d-131">Para adicionar o preenchimento com TAB ao shell do **Bash** na CLI do .NET Core, adicione o seguinte código ao arquivo `.bashrc`:</span><span class="sxs-lookup"><span data-stu-id="e4f7d-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="e4f7d-132">Zsh</span><span class="sxs-lookup"><span data-stu-id="e4f7d-132">Zsh</span></span>

<span data-ttu-id="e4f7d-133">Para adicionar o preenchimento com TAB ao shell do **zsh** na CLI do .NET Core, adicione o seguinte código ao arquivo `.zshrc`:</span><span class="sxs-lookup"><span data-stu-id="e4f7d-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
