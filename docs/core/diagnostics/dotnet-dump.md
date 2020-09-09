---
title: dotnet-despejo-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: e008dcfc734a8742c495ea32a7a149c9a55c54c6
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598103"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="4b2a1-103">Utilitário de coleta e análise de despejo (dotNet-dump)</span><span class="sxs-lookup"><span data-stu-id="4b2a1-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="4b2a1-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4b2a1-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="4b2a1-105">`dotnet-dump` Não tem suporte no macOS.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="install-dotnet-dump"></a><span data-ttu-id="4b2a1-106">Instalar dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="4b2a1-106">Install dotnet-dump</span></span>

<span data-ttu-id="4b2a1-107">Para instalar a versão de lançamento mais recente do `dotnet-dump` [pacote NuGet](https://www.nuget.org/packages/dotnet-dump), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="4b2a1-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="4b2a1-108">Sinopse</span><span class="sxs-lookup"><span data-stu-id="4b2a1-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="4b2a1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b2a1-109">Description</span></span>

<span data-ttu-id="4b2a1-110">A `dotnet-dump` ferramenta global é uma maneira de coletar e analisar despejos do Windows e do Linux sem nenhum depurador nativo envolvido como `lldb` no Linux.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="4b2a1-111">Essa ferramenta é importante em plataformas como o Alpine Linux, onde um trabalho completo `lldb` não está disponível.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="4b2a1-112">A `dotnet-dump` ferramenta permite que você execute comandos SOS para analisar falhas e o GC (coletor de lixo), mas não é um depurador nativo para que não haja suporte para a exibição de quadros de pilha nativos.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="4b2a1-113">Opções</span><span class="sxs-lookup"><span data-stu-id="4b2a1-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="4b2a1-114">Exibe a versão do utilitário dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4b2a1-115">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="4b2a1-116">Comandos</span><span class="sxs-lookup"><span data-stu-id="4b2a1-116">Commands</span></span>

| <span data-ttu-id="4b2a1-117">Comando</span><span class="sxs-lookup"><span data-stu-id="4b2a1-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="4b2a1-118">dotnet-despejo de coleta</span><span class="sxs-lookup"><span data-stu-id="4b2a1-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="4b2a1-119">dotnet-análise de despejo</span><span class="sxs-lookup"><span data-stu-id="4b2a1-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="4b2a1-120">dotnet-despejo de coleta</span><span class="sxs-lookup"><span data-stu-id="4b2a1-120">dotnet-dump collect</span></span>

<span data-ttu-id="4b2a1-121">Captura um despejo de um processo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4b2a1-122">Sinopse</span><span class="sxs-lookup"><span data-stu-id="4b2a1-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="4b2a1-123">Opções</span><span class="sxs-lookup"><span data-stu-id="4b2a1-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="4b2a1-124">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="4b2a1-125">Especifica o número de identificação do processo do qual coletar um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="4b2a1-126">Especifica o tipo de despejo, que determina os tipos de informações que são coletadas do processo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="4b2a1-127">Há três tipos:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-127">There are three types:</span></span>

  - <span data-ttu-id="4b2a1-128">`Full` -O maior despejo que contém toda a memória, incluindo as imagens de módulo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-128">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="4b2a1-129">`Heap` -Um despejo grande e relativamente abrangente contendo listas de módulos, listas de threads, todas as pilhas, informações de exceção, informações de identificador e toda a memória, exceto imagens mapeadas.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-129">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="4b2a1-130">`Mini` -Um despejo pequeno contendo listas de módulos, listas de threads, informações de exceção e todas as pilhas.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-130">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="4b2a1-131">Se não for especificado, `Full` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-131">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="4b2a1-132">O caminho completo e o nome do arquivo em que o despejo coletado deve ser gravado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-132">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="4b2a1-133">Se não for especificado:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-133">If not specified:</span></span>

  - <span data-ttu-id="4b2a1-134">O padrão é *. \ dump_YYYYMMDD_HHMMSS. dmp* no Windows.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-134">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="4b2a1-135">O padrão é *./core_YYYYMMDD_HHMMSS* no Linux.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-135">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="4b2a1-136">AAAAMMDD é ano/mês/dia e HHMMSS é hora/minuto/segundo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-136">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="4b2a1-137">Habilita o log de diagnóstico de coleta de despejo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-137">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="4b2a1-138">dotnet-análise de despejo</span><span class="sxs-lookup"><span data-stu-id="4b2a1-138">dotnet-dump analyze</span></span>

<span data-ttu-id="4b2a1-139">Inicia um shell interativo para explorar um despejo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-139">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="4b2a1-140">O Shell aceita vários [comandos SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="4b2a1-140">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="4b2a1-141">Sinopse</span><span class="sxs-lookup"><span data-stu-id="4b2a1-141">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="4b2a1-142">Argumentos</span><span class="sxs-lookup"><span data-stu-id="4b2a1-142">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="4b2a1-143">Especifica o caminho para o arquivo de despejo a ser analisado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-143">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="4b2a1-144">Opções</span><span class="sxs-lookup"><span data-stu-id="4b2a1-144">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="4b2a1-145">Especifica o [comando](#analyze-sos-commands) a ser executado no Shell em Iniciar.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-145">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="4b2a1-146">Analisar comandos SOS</span><span class="sxs-lookup"><span data-stu-id="4b2a1-146">Analyze SOS commands</span></span>

| <span data-ttu-id="4b2a1-147">Comando</span><span class="sxs-lookup"><span data-stu-id="4b2a1-147">Command</span></span>                             | <span data-ttu-id="4b2a1-148">Função</span><span class="sxs-lookup"><span data-stu-id="4b2a1-148">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="4b2a1-149">Exibe todos os comandos disponíveis</span><span class="sxs-lookup"><span data-stu-id="4b2a1-149">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="4b2a1-150">Exibe o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-150">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="4b2a1-151">Sai do modo interativo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-151">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="4b2a1-152">Fornece um rastreamento de pilha apenas do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-152">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="4b2a1-153">Lista os threads gerenciados em execução.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-153">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="4b2a1-154">Exibe informações sobre máquinas de estado assíncrono no heap coletado por lixo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-154">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="4b2a1-155">Exibe detalhes sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-155">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="4b2a1-156">Exibe informações sobre uma estrutura de classe do EE no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-156">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="4b2a1-157">Exibe informações sobre um delegado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-157">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="4b2a1-158">Exibe informações sobre todos os AppDomains e todos os assemblies nos domínios.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-158">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="4b2a1-159">Exibe informações sobre o heap coletado por lixo e estatísticas de coleção sobre objetos.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-159">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="4b2a1-160">Exibe o MSIL (Microsoft Intermediate Language) associado a um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-160">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="4b2a1-161">Grava o conteúdo de um log de estresse na memória no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-161">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="4b2a1-162">Exibe informações sobre uma estrutura MethodDesc no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-162">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="4b2a1-163">Exibe informações sobre uma estrutura de módulo do EE no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-163">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="4b2a1-164">Exibe informações sobre uma tabela de métodos no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-164">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="4b2a1-165">Exibe informações sobre um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-165">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="4b2a1-166">Exibe todos os objetos gerenciados encontradas dentro dos limites da pilha atual.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-166">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="4b2a1-167">Exibe informações sobre a memória de processo consumida por estruturas de dados de tempo de execução internas.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-167">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="4b2a1-168">Exibe todos os objetos registrados para a finalização.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-168">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="4b2a1-169">Exibe informações sobre referências (ou raízes) para um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-169">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="4b2a1-170">Exibe o local no heap de GC do argumento passado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-170">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="4b2a1-171">Exibe a estrutura MethodDesc no endereço especificado no código JIT.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-171">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="4b2a1-172">Libera todos os recursos usados pela família de comandos `hist*`.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-172">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="4b2a1-173">Inicializa as estruturas de SOS com base no log de estresse salvo no elemento a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-173">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="4b2a1-174">Exibe as realocações de log de estresse da coleta de lixo relacionadas ao `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="4b2a1-174">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="4b2a1-175">Exibe todas as entradas de log que fazem referência a um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-175">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="4b2a1-176">Exibe informações relacionadas a ambas as promoções e realocações da raiz especificada.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-176">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="4b2a1-177">Exibe os módulos nativos no processo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-177">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="4b2a1-178">Exibe a estrutura de MethodTable e a estrutura EEClass para o `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="4b2a1-178">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="4b2a1-179">Exibe qualquer objeto derivado da classe de exceção no endereço `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="4b2a1-179">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="4b2a1-180">Habilita o suporte ao servidor de símbolos</span><span class="sxs-lookup"><span data-stu-id="4b2a1-180">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="4b2a1-181">Exibe as informações do SyncBlock de suporte.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-181">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="4b2a1-182">Define ou exibe a ID de thread atual para os comandos SOS.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-182">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="4b2a1-183">Usando `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="4b2a1-183">Using `dotnet-dump`</span></span>

<span data-ttu-id="4b2a1-184">A primeira etapa é coletar um despejo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-184">The first step is to collect a dump.</span></span> <span data-ttu-id="4b2a1-185">Esta etapa poderá ser ignorada se um dump principal já tiver sido gerado.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-185">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="4b2a1-186">O sistema operacional ou o [recurso de geração de despejo](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) interno do tempo de execução do .NET Core pode criar dumps de núcleo.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-186">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="4b2a1-187">Agora, analise o dump principal com o `analyze` comando:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-187">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="4b2a1-188">Essa ação abre uma sessão interativa que aceita comandos como:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-188">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="4b2a1-189">Para ver uma exceção sem tratamento que eliminou seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-189">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="4b2a1-190">Instruções especiais para o Docker</span><span class="sxs-lookup"><span data-stu-id="4b2a1-190">Special instructions for Docker</span></span>

<span data-ttu-id="4b2a1-191">Se você estiver executando sob o Docker, a coleta de despejo exigirá `SYS_PTRACE` recursos ( `--cap-add=SYS_PTRACE` ou `--privileged` ).</span><span class="sxs-lookup"><span data-stu-id="4b2a1-191">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="4b2a1-192">Em Microsoft .NET principais imagens do Docker do SDK do Linux, alguns `dotnet-dump` comandos podem gerar a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="4b2a1-192">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="4b2a1-193">Exceção sem tratamento: System.DllNotFoundException: não é possível carregar a biblioteca compartilhada ' libdl.so ' ou uma de suas exceções de dependência.</span><span class="sxs-lookup"><span data-stu-id="4b2a1-193">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="4b2a1-194">Para contornar esse problema, instale o pacote "libc6-dev".</span><span class="sxs-lookup"><span data-stu-id="4b2a1-194">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b2a1-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b2a1-195">See also</span></span>

- [<span data-ttu-id="4b2a1-196">Blog sobre coleta e análise de despejos de memória</span><span class="sxs-lookup"><span data-stu-id="4b2a1-196">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="4b2a1-197">Ferramenta de análise de heap (dotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="4b2a1-197">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
