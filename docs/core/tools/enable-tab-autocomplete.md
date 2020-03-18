---
title: Ativar o recurso auto-completar com TAB
description: Este artigo ensina você a habilitar o preenchimento com TAB na CLI do .NET Core para o PowerShell, o Bash e o zsh.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 31328be14811760bc8d7fb527e0d55abfe6b1493
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156745"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="9c5d9-103">Como habilitar o preenchimento com TAB na CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c5d9-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="9c5d9-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="9c5d9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="9c5d9-105">Este artigo descreve como configurar o preenchimento com TAB para três shells: PowerShell, Bash e zsh.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="9c5d9-106">Para outros shells, consulte sua documentação sobre como configurar a conclusão da guia.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="9c5d9-107">Uma vez configurado, a conclusão da guia para `dotnet` o .NET Core CLI é acionada digitando um comando no shell e, em seguida, pressionando a tecla TAB.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="9c5d9-108">A linha de comando atual é enviada para o comando `dotnet complete`, e os resultados são processados pelo shell.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="9c5d9-109">Teste os resultados sem habilitar o preenchimento com TAB enviando algo diretamente para o comando `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="9c5d9-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="9c5d9-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="9c5d9-111">Se esse comando não funcionar, verifique se esse SDK do .NET Core 2.0 ou superior está instalado.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="9c5d9-112">Se ele está instalado, mas esse comando ainda não funciona, verifique se o comando `dotnet` é resolvido para uma versão do SDK do .NET Core 2.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="9c5d9-113">Use o comando `dotnet --version` para ver para qual versão do `dotnet` o caminho atual está sendo resolvido.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="9c5d9-114">Para obter mais informações, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="9c5d9-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9c5d9-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9c5d9-115">Examples</span></span>

<span data-ttu-id="9c5d9-116">Estes são alguns exemplos do que o preenchimento com TAB fornece:</span><span class="sxs-lookup"><span data-stu-id="9c5d9-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="9c5d9-117">Entrada</span><span class="sxs-lookup"><span data-stu-id="9c5d9-117">Input</span></span>                                | <span data-ttu-id="9c5d9-118">se torna</span><span class="sxs-lookup"><span data-stu-id="9c5d9-118">becomes</span></span>                                                                     | <span data-ttu-id="9c5d9-119">porque</span><span class="sxs-lookup"><span data-stu-id="9c5d9-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="9c5d9-120">`add` é o primeiro subcomando, em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="9c5d9-121">O preenchimento com TAB faz a correspondência de subcadeias de caracteres e `--help` vem em primeiro lugar em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="9c5d9-122">Na segunda vez que a tecla TAB é pressionada, a próxima sugestão é exibida.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="9c5d9-123">Os resultados são retornados em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="9c5d9-124">O preenchimento com TAB reconhece o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="9c5d9-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c5d9-125">PowerShell</span></span>

<span data-ttu-id="9c5d9-126">Para adicionar o preenchimento com TAB ao **PowerShell** na CLI do .NET Core, crie ou edite o perfil armazenado na variável `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="9c5d9-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="9c5d9-127">Para obter mais informações, confira [Como criar seu perfil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) e [Perfis e política de execução](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="9c5d9-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="9c5d9-128">Adicione o seguinte código ao seu perfil:</span><span class="sxs-lookup"><span data-stu-id="9c5d9-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="9c5d9-129">bash</span><span class="sxs-lookup"><span data-stu-id="9c5d9-129">bash</span></span>

<span data-ttu-id="9c5d9-130">Para adicionar o preenchimento com TAB ao shell do **Bash** na CLI do .NET Core, adicione o seguinte código ao arquivo `.bashrc`:</span><span class="sxs-lookup"><span data-stu-id="9c5d9-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="9c5d9-131">zsh</span><span class="sxs-lookup"><span data-stu-id="9c5d9-131">zsh</span></span>

<span data-ttu-id="9c5d9-132">Para adicionar o preenchimento com TAB ao shell do **zsh** na CLI do .NET Core, adicione o seguinte código ao arquivo `.zshrc`:</span><span class="sxs-lookup"><span data-stu-id="9c5d9-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
