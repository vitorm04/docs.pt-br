---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória.
ms.date: 11/13/2019
ms.topic: reference
ms.openlocfilehash: 220b94e92f61fd44d2ab13291e41b8007a287cc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428706"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opções de configuração de tempo de execução para coleta de lixo

Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução. Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações. No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.

As configurações são organizadas em grupos nesta página. As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.

> [!NOTE]
>
> - Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.
> - Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design. Essas configurações são omitidas desta página.
> - Para valores numéricos, use a notação decimal para as configurações no arquivo *runtimeconfig. JSON* e notação hexadecimal para configurações de variável de ambiente.

## <a name="flavors-of-garbage-collection"></a>Tipos de coleta de lixo

Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor. Para obter mais informações sobre as diferenças entre os dois, consulte [conceitos básicos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Os subtipos de coleta de lixo são em segundo plano e não simultâneos.

Use as seguintes configurações para selecionar tipos de coleta de lixo:

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.
- Padrão: coleta de lixo da estação de trabalho (`false`).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false`-estação de trabalho<br/>servidor de `true` | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcServer` | 0-estação de trabalho<br/>1-servidor | .NET Core 1.0 |
| **App. config para .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-estação de trabalho<br/>servidor de `true` |  |

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. simultaneamente/COMPlus_gcConcurrent

- Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.
- Padrão: habilitado (`true`).
- Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) e [coleta de lixo do servidor em segundo plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | GC de `true` em segundo plano<br/>`false`-GC não simultâneo | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcConcurrent` | GC de `true` em segundo plano<br/>`false`-GC não simultâneo | .NET Core 1.0 |
| **App. config para .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | GC de `true` em segundo plano<br/>`false`-GC não simultâneo |  |

## <a name="manage-resource-usage"></a>Gerenciar o uso de recursos

Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.

Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Limita o número de heaps criados pelo coletor de lixo.
- Aplica-se somente à coleta de lixo do servidor (GC).
- Se a afinidade do processador GC estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros processadores de `n`. (Use a máscara relacionar ou as configurações de intervalos de relacionar para especificar exatamente quais processadores relacionar.)
- Se a afinidade do processador GC estiver desabilitada, essa configuração limitará o número de heaps do GC.
- Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapCount` | *valor hexadecimal* | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valor decimal* | 4.6.2 |

> [!TIP]
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 10 para a variável de ambiente.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Especifica os processadores exatos que os threads do coletor de lixo devem usar.
- Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.
- Aplica-se somente à coleta de lixo do servidor (GC).
- O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo. Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária. Isso especifica que os primeiros 10 processadores devem ser usados. Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeMask` | *valor hexadecimal* | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valor decimal* | 4.6.2 |

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Especifica a lista de processadores a serem usados para threads do coletor de lixo.
- Essa configuração é semelhante à `System.GC.HeapAffinitizeMask`, exceto pelo fato de que ela permite que você especifique mais de 64 processadores.
- Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".
- Se a afinidade do processador estiver desabilitada ao definir `System.GC.NoAffinitize` como `true`, essa configuração será ignorada.
- Aplica-se somente à coleta de lixo do servidor (GC).
- Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Lista separada por vírgulas de números de processador ou intervalos de números de processador.<br/>Exemplo de UNIX: "1-10, 12, 50-52, 70"<br/>Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeRanges` | Lista separada por vírgulas de números de processador ou intervalos de números de processador.<br/>Exemplo de UNIX: "1-10, 12, 50-52, 70"<br/>Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.

  Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU. O coletor de lixo usa todos os núcleos para criar e balancear heaps.

- Aplica-se à coleta de lixo do servidor (GC) somente em sistemas de operação do Windows de 64 bits.
- Padrão: desabilitado (0).
- Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_GCCpuGroup` | 0-desabilitado<br/>1-habilitado | .NET Core 1.0 |
| **App. config para .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-desabilitado<br/>habilitado para `true` |  |

> [!NOTE]
> Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de ambiente `COMPlus_Thread_UseAllCpuGroups` como `1`.

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores. Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica. Um heap é criado para cada thread do GC.
- Aplica-se somente à coleta de lixo do servidor (GC).
- Padrão: relacionar os threads de coleta de lixo com processadores (`false`).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false`-relacionar<br/>`true`-não relacionar | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCNoAffinitize` | 0-relacionar<br/>1-não relacionar | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-relacionar<br/>`true`-não relacionar | 4.6.2 |

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapHardLimit` | *valor hexadecimal* | .NET Core 3.0 |

> [!TIP]
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para especificar um limite rígido de heap de 80.000 bytes, os valores seriam 80000 para o arquivo JSON e 13880 para a variável de ambiente.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Especifica o uso de heap do GC como uma porcentagem da memória total.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapHardLimitPercent` | *valor hexadecimal* | .NET Core 3.0 |

> [!TIP]
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o uso de heap para 30%, os valores seriam 30 para o arquivo JSON e 1E para a variável de ambiente.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).
- Padrão: liberar segmentos de volta para o sistema operacional (`false`).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false`-versão para o sistema operacional<br/>`true`-Put em espera| .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_GCRetainVM` | 0-liberar para o sistema operacional<br/>1-colocar em espera | .NET Core 1.0 |

## <a name="large-pages"></a>Páginas grandes

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.
- Padrão: desabilitado (0).
- Essa é uma configuração experimental.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_GCLargePages` | 0-desabilitado<br/>1-habilitado | .NET Core 3.0 |

## <a name="large-objects"></a>Objetos grandes

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.
- Padrão: habilitado (1).
- Essa opção pode se tornar obsoleta em uma versão futura do .NET.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_gcAllowVeryLargeObjects` | 1-habilitado<br/> 0-desabilitado | .NET Core 1.0 |
| **App. config para .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | 1-habilitado<br/> 0-desabilitado | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Limite de heap de objeto grande

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System. GC. LOHThreshold/COMPlus_GCLOHThreshold

- Especifica o tamanho do limite, em bytes, que faz com que os objetos vá para o LOH (heap de objeto grande).
- O limite padrão é de 85.000 bytes.
- O valor especificado deve ser maior que o limite padrão.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.LOHThreshold` | *valor decimal* | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_GCLOHThreshold` | *valor hexadecimal* | .NET Core 1.0 |
| **App. config para .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *valor decimal* | .NET Framework 4.8 |

> [!TIP]
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 1D4C0 para a variável de ambiente.

## <a name="standalone-gc"></a>GC autônomo

### <a name="complus_gcname"></a>COMPlus_GCName

- Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.
- Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/standalone-gc-loading.md).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} | {1&gt;N/A&lt;1} |
| **Variável de ambiente** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
