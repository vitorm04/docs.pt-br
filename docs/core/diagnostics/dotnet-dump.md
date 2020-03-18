---
title: dotnet-dump - .NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: 3c0e28d4efc96ae53ec7dfae243725ab400e6b8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737663"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Utilitário de coleta`dotnet-dump`e análise de despejo ( )

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

> [!NOTE]
> `dotnet-dump`não é suportado no macOS.

## <a name="installing-dotnet-dump"></a>Instalando o `dotnet-dump`

Para instalar a versão `dotnet-dump` de versão mais recente do [pacote NuGet,](https://www.nuget.org/packages/dotnet-dump)use o comando [dotnet tool install:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Sinopse

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Descrição

A `dotnet-dump` ferramenta global é uma maneira de coletar e analisar dumps `lldb` do Windows e Linux sem qualquer depurador nativo envolvido, como no Linux. Esta ferramenta é importante em plataformas como `lldb` alpine Linux onde um pleno funcionamento não está disponível. A `dotnet-dump` ferramenta permite que você execute comandos SOS para analisar falhas e o coletor de lixo (GC), mas não é um depurador nativo, então coisas como exibir quadros de pilha nativa não são suportados.

## <a name="options"></a>Opções

- **`--version`**

  Exibe a versão do utilitário dotnet-counters.

- **`-h|--help`**

  Mostra ajuda na linha de comando.

## <a name="commands"></a>Comandos

| Comando                                     |
| ------------------------------------------- |
| [dotnet-dump coletar](#dotnet-dump-collect) |
| [dotnet-dump analisar](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-dump coletar

Captura um lixão de um processo.

### <a name="synopsis"></a>Sinopse

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Opções

- **`-h|--help`**

  Mostra ajuda na linha de comando.

- **`-p|--process-id <PID>`**

  Especifica o número de id do processo para coletar um dump de memória.

- **`--type <Heap|Mini>`**

  Especifica o tipo de despejo, que determina os tipos de informações coletadas do processo. Existem dois tipos:

  - `Heap`- Um despejo grande e relativamente abrangente contendo listas de módulos, listas de segmentos, todas as pilhas, informações de exceção, informações de manuseio e toda a memória, exceto imagens mapeadas.
  - `Mini`- Um pequeno dump contendo listas de módulos, listas de segmentos, informações de exceção e todas as pilhas.

  Se não for `Heap` especificado, é o padrão.

- **`-o|--output <output_dump_path>`**

  O caminho completo e o nome do arquivo onde o dump coletado deve ser escrito.

  Se não for especificado:

  - Padrão para *.\dump_YYYYMMDD_HHMMSS.dmp* no Windows.
  - Padrão para *./core_YYYYMMDD_HHMMSS* no Linux.

  YYYYMMDD é Ano/Mês/Dia e HHMMSS é Hora/Minuto/Segundo.

- **`--diag`**

  Permite o registro de diagnóstico de coleta de despejo.

## <a name="dotnet-dump-analyze"></a>dotnet-dump analisar

Começa uma concha interativa para explorar um lixão. O shell aceita vários [comandos SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Sinopse

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Argumentos

- **`<dump_path>`**

  Especifica o caminho para o arquivo de despejo a ser analisado.

### <a name="options"></a>Opções

- **`-c|--command <debug_command>`**

  Especifica o [comando](#analyze-sos-commands) para executar no shell no início.

### <a name="analyze-sos-commands"></a>Analisar comandos SOS

| Comando                             | Função                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Exibe todos os comandos disponíveis                                                               |
| `soshelp|help <command>`            | Exibe o comando especificado.                                                               |
| `exit|quit`                         | Sai do modo interativo.                                                                       |
| `clrstack <arguments>`              | Fornece um rastreamento de pilha apenas do código gerenciado.                                                  |
| `clrthreads <arguments>`            | Lista os segmentos gerenciados em execução.                                                            |
| `dumpasync <arguments>`             | Exibe informações sobre máquinas de estado de asincronização no monte coletado de lixo.                |
| `dumpassembly <arguments>`          | Exibe detalhes sobre uma montagem.                                                           |
| `dumpclass <arguments>`             | Exibe informações sobre uma estrutura de classe EE no endereço especificado.                     |
| `dumpdelegate <arguments>`          | Exibe informações sobre um delegado.                                                        |
| `dumpdomain <arguments>`            | Exibe todas as informações do AppDomains e todos os conjuntos dentro dos domínios.                |
| `dumpheap <arguments>`              | Exibe informações sobre o monte coletado de lixo e estatísticas de coleta sobre objetos.       |
| `dumpil <arguments>`                | Exibe o MSIL (Microsoft Intermediate Language) associado a um método gerenciado. |
| `dumplog <arguments>`               | Grava o conteúdo de um log de estresse na memória no arquivo especificado.                         |
| `dumpmd <arguments>`                | Exibe informações sobre uma estrutura MethodDesc no endereço especificado.                   |
| `dumpmodule <arguments>`            | Exibe informações sobre uma estrutura de módulo EE no endereço especificado.                    |
| `dumpmt <arguments>`                | Exibe informações sobre uma tabela de métodos no endereço especificado.                           |
| `dumpobj <arguments>`               | Exibe informações sobre um objeto no endereço especificado.                                       |
| `dso|dumpstackobjects <arguments>`  | Exibe todos os objetos gerenciados encontradas dentro dos limites da pilha atual.                    |
| `eeheap <arguments>`                | Exibe informações sobre a memória do processo consumida por estruturas internas de dados em tempo de execução.              |
| `finalizequeue <arguments>`         | Exibe todos os objetos registrados para a finalização.                                             |
| `gcroot <arguments>`                | Exibe informações sobre referências (ou raízes) a um objeto no endereço especificado.              |
| `gcwhere <arguments>`               | Exibe a localização no monte GC do argumento aprovado.                               |
| `ip2md <arguments>`                 | Exibe a estrutura MethodDesc no endereço especificado no código JIT.                       |
| `histclear <arguments>`             | Libera todos os recursos usados pela família de comandos `hist*`.                                |
| `histinit <arguments>`              | Inicializa as estruturas de SOS com base no log de estresse salvo no elemento a ser depurado.                     |
| `histobj <arguments>`               | Exibe as realocação de troncos de estresse de coleta de lixo relacionadas a `<arguments>`.              |
| `histobjfind <arguments>`           | Exibe todas as entradas de log que fazem referência a um objeto no endereço especificado.               |
| `histroot <arguments>`              | Exibe informações relacionadas a ambas as promoções e realocações da raiz especificada.        |
| `lm|modules`                        | Exibe os módulos nativos no processo.                                                   |
| `name2ee <arguments>`               | Exibe a estrutura MethodTable e a `<argument>`estrutura EEClass para o .                |
| `pe|printexception <arguments>`     | Exibe qualquer objeto derivado da classe `<argument>`Exceção no endereço .             |
| `setsymbolserver <arguments>`       | Habilita o suporte ao servidor de símbolos                                                             |
| `syncblk <arguments>`               | Exibe as informações do suporte do SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Define ou exibe o ID de thread atual para os comandos SOS.                                  |

## <a name="using-dotnet-dump"></a>Usando o `dotnet-dump`

O primeiro passo é recolher uma lixeira. Esta etapa pode ser ignorada se um despejo de núcleo já tiver sido gerado. O sistema operacional ou o recurso de geração de [despejo](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) incorporado do .NET Core podem criar dumps de núcleo.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Agora analise o `analyze` despejo do núcleo com o comando:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Esta ação traz à tona uma sessão interativa que aceita comandos como:

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

Para ver uma exceção não manuseada que matou seu aplicativo:

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

## <a name="special-instructions-for-docker"></a>Instruções especiais para Docker

Se você estiver executando o Docker, a`--cap-add=SYS_PTRACE` `--privileged`coleta de lixo requer `SYS_PTRACE` recursos (ou ).

Nas imagens do Microsoft .NET Core `dotnet-dump` SDK Linux Docker, alguns comandos podem abrir a seguinte exceção:

> Exceção não manuseada: System.DllNotFoundException: Não é possível carregar a biblioteca compartilhada 'libdl.so' ou uma das exceções de suas dependências.

Para contornar esse problema, instale o pacote "libc6-dev".
