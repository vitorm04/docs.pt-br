---
title: Depurar um tutorial de vazamento de memória
description: Saiba como depurar um vazamento de memória no .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737734"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Tutorial: Depurar um vazamento de memória no .NET Core

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

Este tutorial demonstra as ferramentas para analisar um vazamento de memória .NET Core.

Este tutorial usa um aplicativo de exemplo, que foi projetado para vazar intencionalmente a memória. A amostra é fornecida como um exercício. Você pode analisar um aplicativo que está vazando memória involuntariamente também.

Neste tutorial, você irá:

> [!div class="checklist"]
>
> - Examine o uso gerenciado da memória com [contadores de dotnet](dotnet-counters.md).
> - Gerar um arquivo de despejo.
> - Analise o uso da memória usando o arquivo de despejo.

## <a name="prerequisites"></a>Pré-requisitos

O tutorial usa:

- [SDK do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.
- [dotnet-trace](dotnet-trace.md) para processos de lista.
- [contadores dotnet](dotnet-counters.md) para verificar o uso gerenciado da memória.
- [dotnet-dump](dotnet-dump.md) para coletar e analisar um arquivo de despejo.
- Um aplicativo [de destino de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) para diagnosticar.

O tutorial pressupõe que a amostra e as ferramentas estão instaladas e prontas para uso.

## <a name="examine-managed-memory-usage"></a>Examine o uso gerenciado da memória

Antes de começar a coletar dados de diagnóstico para nos ajudar a criar esse cenário, você precisa ter certeza de que está realmente vendo um vazamento de memória (crescimento de memória). Você pode usar a ferramenta [dotnet-counters](dotnet-counters.md) para confirmar isso.

Abra uma janela do console e navegue até o diretório onde você baixou e descompactou o [alvo de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Executar o alvo:

```dotnetcli
dotnet run
```

A partir de um console separado, encontre o ID do processo usando a ferramenta [dotnet-trace:](dotnet-trace.md)

```console
dotnet-trace ps
```

A saída deve ser semelhante a:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Agora, verifique o uso gerenciado da memória com a ferramenta [dotnet-counters.](dotnet-counters.md) O `--refresh-interval` especifica o número de segundos entre as atualizações:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

A saída ao vivo deve ser semelhante a:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Focando nesta linha:

```console
    GC Heap Size (MB)                                  4
```

Você pode ver que a memória de pilha gerenciada é de 4 MB logo após a inicialização.

Agora, aperte `http://localhost:5000/api/diagscenario/memleak/20000`a URL .

Observe que o uso da memória cresceu para 30 MB.

```console
    GC Heap Size (MB)                                 30
```

Observando o uso da memória, você pode dizer com segurança que a memória está crescendo ou vazando. O próximo passo é coletar os dados certos para análise de memória.

### <a name="generate-memory-dump"></a>Gerar despejo de memória

Ao analisar possíveis vazamentos de memória, você precisa acessar o monte de memória do aplicativo. Então você pode analisar o conteúdo da memória. Olhando para as relações entre objetos, você cria teorias sobre por que a memória não está sendo liberada. Uma fonte de dados de diagnóstico comum é um despejo de memória no Windows ou o despejo de núcleo equivalente no Linux. Para gerar um dump de um aplicativo .NET Core, você pode usar a ferramenta [dotnet-dump).](dotnet-dump.md)

Usando o [destino de depuração de amostra](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) iniciado anteriormente, execute o seguinte comando para gerar um dump do núcleo do Linux:

```dotnetcli
dotnet-dump collect -p 4807
```

O resultado é um despejo de núcleo localizado na mesma pasta.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Reiniciar o processo de falha

Uma vez que o despejo é coletado, você deve ter informações suficientes para diagnosticar o processo falho. Se o processo de falha está sendo executado em um servidor de produção, agora é o momento ideal para remediação a curto prazo, reiniciando o processo.

Neste tutorial, você está pronto com o [destino de depuração Sample](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) e você pode fechá-lo. Navegue até o terminal que `Control-C`iniciou o servidor e pressione .

### <a name="analyze-the-core-dump"></a>Analisar o despejo do núcleo

Agora que você tem um dump de núcleo gerado, use a ferramenta [dotnet-dump)](dotnet-dump.md) para analisar o dump:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Onde `core_20190430_185145` está o nome do despejo do núcleo que você quer analisar.

> [!NOTE]
> Se você vir um erro reclamando que *libdl.so* não pode ser encontrado, você pode ter que instalar o pacote *libc6-dev.* Para saber mais, confira [Pré-requisitos para o .NET Core no Linux](../linux-prerequisites.md).

Você será apresentado com um prompt onde você pode inserir comandos SOS. Geralmente, a primeira coisa que você quer olhar é o estado geral do monte gerenciado:

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

Aqui você pode ver que `String` `Customer` a maioria dos objetos são ou objetos.

Você pode `dumpheap` usar o comando novamente com a tabela de métodos (MT) para obter uma lista de todas as `String` instâncias:

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Agora você pode `gcroot` usar `System.String` o comando em uma instância para ver como e por que o objeto está enraizado. Seja paciente porque este comando leva vários minutos com um monte de 30 MB:

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Você pode ver `String` que o `Customer` é diretamente mantido pelo `CustomerCache` objeto e indiretamente mantido por um objeto.

Você pode continuar despejando objetos para ver que a maioria dos `String` objetos segue um padrão semelhante. Neste ponto, a investigação forneceu informações suficientes para identificar a causa raiz em seu código.

Este procedimento geral permite identificar a fonte de grandes vazamentos de memória.

## <a name="clean-up-resources"></a>Limpar recursos

Neste tutorial, você começou um servidor web de exemplo. Este servidor deveria ter sido desligado conforme explicado na seção Reiniciar a seção [de processo com falha.](#restart-the-failed-process)

Você também pode excluir o arquivo de despejo que foi criado.

## <a name="next-steps"></a>Próximas etapas

Parabéns por completar este tutorial.

Ainda estamos publicando mais tutoriais de diagnóstico. Você pode ler as versões de rascunho no repositório [dotnet/diagnóstico.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

Este tutorial cobriu o básico das principais ferramentas de diagnóstico .NET. Para uso avançado, consulte a seguinte documentação de referência:

* [dotnet-trace](dotnet-trace.md) para processos de lista.
* [contadores dotnet](dotnet-counters.md) para verificar o uso gerenciado da memória.
* [dotnet-dump](dotnet-dump.md) para coletar e analisar um arquivo de despejo.
