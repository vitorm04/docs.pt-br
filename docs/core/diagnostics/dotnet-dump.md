---
title: dotnet-despejo-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: 5489011538a4a11d60b333f0230a718c88722c97
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140926"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="d46c3-103">Utilitário de coleta e análise de despejo (dotNet-dump)</span><span class="sxs-lookup"><span data-stu-id="d46c3-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="d46c3-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d46c3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="d46c3-105">`dotnet-dump` Não tem suporte no macOS.</span><span class="sxs-lookup"><span data-stu-id="d46c3-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="install-dotnet-dump"></a><span data-ttu-id="d46c3-106">Instalar dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="d46c3-106">Install dotnet-dump</span></span>

<span data-ttu-id="d46c3-107">Para instalar a versão de lançamento mais recente do `dotnet-dump` [pacote NuGet](https://www.nuget.org/packages/dotnet-dump), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="d46c3-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="d46c3-108">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d46c3-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="d46c3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d46c3-109">Description</span></span>

<span data-ttu-id="d46c3-110">A `dotnet-dump` ferramenta global é uma maneira de coletar e analisar despejos do Windows e do Linux sem nenhum depurador nativo envolvido como `lldb` no Linux.</span><span class="sxs-lookup"><span data-stu-id="d46c3-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="d46c3-111">Essa ferramenta é importante em plataformas como o Alpine Linux, onde um trabalho completo `lldb` não está disponível.</span><span class="sxs-lookup"><span data-stu-id="d46c3-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="d46c3-112">A `dotnet-dump` ferramenta permite que você execute comandos SOS para analisar falhas e o GC (coletor de lixo), mas não é um depurador nativo para que não haja suporte para a exibição de quadros de pilha nativos.</span><span class="sxs-lookup"><span data-stu-id="d46c3-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="d46c3-113">Opções</span><span class="sxs-lookup"><span data-stu-id="d46c3-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="d46c3-114">Exibe a versão do utilitário dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="d46c3-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d46c3-115">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d46c3-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="d46c3-116">Comandos</span><span class="sxs-lookup"><span data-stu-id="d46c3-116">Commands</span></span>

| <span data-ttu-id="d46c3-117">Comando</span><span class="sxs-lookup"><span data-stu-id="d46c3-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="d46c3-118">dotnet-despejo de coleta</span><span class="sxs-lookup"><span data-stu-id="d46c3-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="d46c3-119">dotnet-análise de despejo</span><span class="sxs-lookup"><span data-stu-id="d46c3-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="d46c3-120">dotnet-despejo de coleta</span><span class="sxs-lookup"><span data-stu-id="d46c3-120">dotnet-dump collect</span></span>

<span data-ttu-id="d46c3-121">Captura um despejo de um processo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d46c3-122">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d46c3-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="d46c3-123">Opções</span><span class="sxs-lookup"><span data-stu-id="d46c3-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d46c3-124">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d46c3-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="d46c3-125">Especifica o número de identificação do processo do qual coletar um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="d46c3-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="d46c3-126">Especifica o tipo de despejo, que determina os tipos de informações que são coletadas do processo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="d46c3-127">Há dois tipos:</span><span class="sxs-lookup"><span data-stu-id="d46c3-127">There are two types:</span></span>

  - <span data-ttu-id="d46c3-128">`Heap` -Um despejo grande e relativamente abrangente contendo listas de módulos, listas de threads, todas as pilhas, informações de exceção, informações de identificador e toda a memória, exceto imagens mapeadas.</span><span class="sxs-lookup"><span data-stu-id="d46c3-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="d46c3-129">`Mini` -Um despejo pequeno contendo listas de módulos, listas de threads, informações de exceção e todas as pilhas.</span><span class="sxs-lookup"><span data-stu-id="d46c3-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="d46c3-130">Se não for especificado, `Heap` será o padrão.</span><span class="sxs-lookup"><span data-stu-id="d46c3-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="d46c3-131">O caminho completo e o nome do arquivo em que o despejo coletado deve ser gravado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="d46c3-132">Se não for especificado:</span><span class="sxs-lookup"><span data-stu-id="d46c3-132">If not specified:</span></span>

  - <span data-ttu-id="d46c3-133">O padrão é *. \ dump_YYYYMMDD_HHMMSS. dmp* no Windows.</span><span class="sxs-lookup"><span data-stu-id="d46c3-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="d46c3-134">O padrão é *./core_YYYYMMDD_HHMMSS* no Linux.</span><span class="sxs-lookup"><span data-stu-id="d46c3-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="d46c3-135">AAAAMMDD é ano/mês/dia e HHMMSS é hora/minuto/segundo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="d46c3-136">Habilita o log de diagnóstico de coleta de despejo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="d46c3-137">dotnet-análise de despejo</span><span class="sxs-lookup"><span data-stu-id="d46c3-137">dotnet-dump analyze</span></span>

<span data-ttu-id="d46c3-138">Inicia um shell interativo para explorar um despejo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="d46c3-139">O Shell aceita vários [comandos SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="d46c3-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="d46c3-140">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d46c3-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="d46c3-141">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d46c3-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="d46c3-142">Especifica o caminho para o arquivo de despejo a ser analisado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="d46c3-143">Opções</span><span class="sxs-lookup"><span data-stu-id="d46c3-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="d46c3-144">Especifica o [comando](#analyze-sos-commands) a ser executado no Shell em Iniciar.</span><span class="sxs-lookup"><span data-stu-id="d46c3-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="d46c3-145">Analisar comandos SOS</span><span class="sxs-lookup"><span data-stu-id="d46c3-145">Analyze SOS commands</span></span>

| <span data-ttu-id="d46c3-146">Comando</span><span class="sxs-lookup"><span data-stu-id="d46c3-146">Command</span></span>                             | <span data-ttu-id="d46c3-147">Função</span><span class="sxs-lookup"><span data-stu-id="d46c3-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="d46c3-148">Exibe todos os comandos disponíveis</span><span class="sxs-lookup"><span data-stu-id="d46c3-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="d46c3-149">Exibe o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="d46c3-150">Sai do modo interativo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="d46c3-151">Fornece um rastreamento de pilha apenas do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="d46c3-152">Lista os threads gerenciados em execução.</span><span class="sxs-lookup"><span data-stu-id="d46c3-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="d46c3-153">Exibe informações sobre máquinas de estado assíncrono no heap coletado por lixo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="d46c3-154">Exibe detalhes sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="d46c3-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="d46c3-155">Exibe informações sobre uma estrutura de classe do EE no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="d46c3-156">Exibe informações sobre um delegado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="d46c3-157">Exibe informações sobre todos os AppDomains e todos os assemblies nos domínios.</span><span class="sxs-lookup"><span data-stu-id="d46c3-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="d46c3-158">Exibe informações sobre o heap coletado por lixo e estatísticas de coleção sobre objetos.</span><span class="sxs-lookup"><span data-stu-id="d46c3-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="d46c3-159">Exibe o MSIL (Microsoft Intermediate Language) associado a um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="d46c3-160">Grava o conteúdo de um log de estresse na memória no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="d46c3-161">Exibe informações sobre uma estrutura MethodDesc no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="d46c3-162">Exibe informações sobre uma estrutura de módulo do EE no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="d46c3-163">Exibe informações sobre uma tabela de métodos no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="d46c3-164">Exibe informações sobre um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="d46c3-165">Exibe todos os objetos gerenciados encontradas dentro dos limites da pilha atual.</span><span class="sxs-lookup"><span data-stu-id="d46c3-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="d46c3-166">Exibe informações sobre a memória de processo consumida por estruturas de dados de tempo de execução internas.</span><span class="sxs-lookup"><span data-stu-id="d46c3-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="d46c3-167">Exibe todos os objetos registrados para a finalização.</span><span class="sxs-lookup"><span data-stu-id="d46c3-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="d46c3-168">Exibe informações sobre referências (ou raízes) para um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="d46c3-169">Exibe o local no heap de GC do argumento passado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="d46c3-170">Exibe a estrutura MethodDesc no endereço especificado no código JIT.</span><span class="sxs-lookup"><span data-stu-id="d46c3-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="d46c3-171">Libera todos os recursos usados pela família de comandos `hist*`.</span><span class="sxs-lookup"><span data-stu-id="d46c3-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="d46c3-172">Inicializa as estruturas de SOS com base no log de estresse salvo no elemento a ser depurado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="d46c3-173">Exibe as realocações de log de estresse da coleta de lixo relacionadas ao `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="d46c3-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="d46c3-174">Exibe todas as entradas de log que fazem referência a um objeto no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="d46c3-175">Exibe informações relacionadas a ambas as promoções e realocações da raiz especificada.</span><span class="sxs-lookup"><span data-stu-id="d46c3-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="d46c3-176">Exibe os módulos nativos no processo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="d46c3-177">Exibe a estrutura de MethodTable e a estrutura EEClass para o `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="d46c3-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="d46c3-178">Exibe qualquer objeto derivado da classe de exceção no endereço `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="d46c3-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="d46c3-179">Habilita o suporte ao servidor de símbolos</span><span class="sxs-lookup"><span data-stu-id="d46c3-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="d46c3-180">Exibe as informações do SyncBlock de suporte.</span><span class="sxs-lookup"><span data-stu-id="d46c3-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="d46c3-181">Define ou exibe a ID de thread atual para os comandos SOS.</span><span class="sxs-lookup"><span data-stu-id="d46c3-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="d46c3-182">Usando `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="d46c3-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="d46c3-183">A primeira etapa é coletar um despejo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-183">The first step is to collect a dump.</span></span> <span data-ttu-id="d46c3-184">Esta etapa poderá ser ignorada se um dump principal já tiver sido gerado.</span><span class="sxs-lookup"><span data-stu-id="d46c3-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="d46c3-185">O sistema operacional ou o [recurso de geração de despejo](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) interno do tempo de execução do .NET Core pode criar dumps de núcleo.</span><span class="sxs-lookup"><span data-stu-id="d46c3-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="d46c3-186">Agora, analise o dump principal com o `analyze` comando:</span><span class="sxs-lookup"><span data-stu-id="d46c3-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="d46c3-187">Essa ação abre uma sessão interativa que aceita comandos como:</span><span class="sxs-lookup"><span data-stu-id="d46c3-187">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="d46c3-188">Para ver uma exceção sem tratamento que eliminou seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d46c3-188">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="d46c3-189">Instruções especiais para o Docker</span><span class="sxs-lookup"><span data-stu-id="d46c3-189">Special instructions for Docker</span></span>

<span data-ttu-id="d46c3-190">Se você estiver executando sob o Docker, a coleta de despejo exigirá `SYS_PTRACE` recursos ( `--cap-add=SYS_PTRACE` ou `--privileged` ).</span><span class="sxs-lookup"><span data-stu-id="d46c3-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="d46c3-191">Em Microsoft .NET principais imagens do Docker do SDK do Linux, alguns `dotnet-dump` comandos podem gerar a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="d46c3-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="d46c3-192">Exceção sem tratamento: System.DllNotFoundException: não é possível carregar a biblioteca compartilhada ' libdl.so ' ou uma de suas exceções de dependência.</span><span class="sxs-lookup"><span data-stu-id="d46c3-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="d46c3-193">Para contornar esse problema, instale o pacote "libc6-dev".</span><span class="sxs-lookup"><span data-stu-id="d46c3-193">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="d46c3-194">Confira também</span><span class="sxs-lookup"><span data-stu-id="d46c3-194">See also</span></span>

- [<span data-ttu-id="d46c3-195">Blog sobre coleta e análise de despejos de memória</span><span class="sxs-lookup"><span data-stu-id="d46c3-195">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="d46c3-196">Ferramenta de análise de heap (dotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="d46c3-196">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
