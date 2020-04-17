---
title: Configurações de configuração de coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607804"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opções de configuração em tempo de execução para coleta de lixo

Esta página contém informações sobre configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução. Se você está tentando alcançar o máximo de desempenho de um aplicativo em execução, considere usar essas configurações. No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.

As configurações são organizadas em grupos nesta página. As configurações dentro de cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.

> [!NOTE]
>
> - Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está sendo executado, de modo que quaisquer configurações de tempo de execução que você definir podem ser substituídas.
> - Algumas configurações, como o [nível de latência,](../../standard/garbage-collection/latency.md)são normalmente definidas apenas através da API na hora do projeto. Essas configurações são omitidas desta página.
> - Para valores numério, use notação decimal para configurações no arquivo *runtimeconfig.json* e notação hexadecimal para configurações variáveis de ambiente. Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".

## <a name="flavors-of-garbage-collection"></a>Sabores da coleta de lixo

Os dois principais sabores da coleta de lixo são a Estação de Trabalho GC e o servidor GC. Para obter mais informações sobre as diferenças entre os dois, consulte [Fundamentos da coleta de lixo](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).

Os subsabores da coleta de lixo são de fundo e não são concomitantes.

Use as seguintes configurações para selecionar sabores de coleta de lixo:

### <a name="systemgcservercomplus_gcserver"></a>System.GC.Server/COMPlus_gcServer

- Configura se o aplicativo usa coleta de lixo da estação de trabalho ou coleta de lixo do servidor.
- Padrão: Coleta de`false`lixo da estação de trabalho ( ).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Server` | `false`- estação de trabalho<br/>`true`- servidor | .NET Core 1.0 |
| **Propriedade MSBuild** | `ServerGarbageCollection` | `false`- estação de trabalho<br/>`true`- servidor | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcServer` | `0`- estação de trabalho<br/>`1`- servidor | .NET Core 1.0 |
| **app.config para .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`- estação de trabalho<br/>`true`- servidor |  |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System.GC.Simultânea/COMPlus_gcConcurrent

- Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.
- Padrão: Ativado`true`().
- Para obter mais informações, consulte [Coleta de lixo em segundo](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) plano e coleta de lixo do servidor em segundo [plano](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.Concurrent` | `true`- fundo GC<br/>`false`- GC não simultâneo | .NET Core 1.0 |
| **Propriedade MSBuild** | `ConcurrentGarbageCollection` | `true`- fundo GC<br/>`false`- GC não simultâneo | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcConcurrent` | `true`- fundo GC<br/>`false`- GC não simultâneo | .NET Core 1.0 |
| **app.config para .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`- fundo GC<br/>`false`- GC não simultâneo |  |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Gerenciar o uso de recursos

Use as configurações descritas nesta seção para gerenciar o uso da memória e do processador do coletor de lixo.

Para obter mais informações sobre algumas dessas configurações, consulte o meio termo entre a [estação de trabalho e a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) entrada do blog gc do servidor.

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System.GC.Heapcount/COMPlus_GCHeapCount

- Limita o número de montes criados pelo coletor de lixo.
- Aplica-se apenas à coleta de lixo do servidor.
- Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver ativada, que é `n` o padrão, a configuração `n` de contagem de pilhas adiaos pilhas/threads GC para os primeiros processadores. (Use as configurações de [intervalos de afeitização](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou [aderiss para](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) especificar exatamente quais processadores aparticipar.)
- Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração limita o número de pilhas gc.
- Para obter mais informações, consulte as observações do [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapCount` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapCount` | *valor hexadecimal* | .NET Core 3.0 |
| **app.config para .NET Framework** | [GCHeapcount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valor decimal* | .NET Framework 4.6.2 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o número de pilhas a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável ambiente.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Especifica os processadores exatos que os segmentos coletores de lixo devem usar.
- Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.
- Aplica-se apenas à coleta de lixo do servidor.
- O valor é uma máscara de bit que define os processadores disponíveis para o processo. Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável ambiente) é 0011 1111 1111 em notação binária. Isso especifica que os primeiros 10 processadores devem ser usados. Para especificar os próximos 10 processadores, ou seja, processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que equivale a um valor binário de 1111 1111 1100 0000 0000.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapAffinitizeMask` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeMask` | *valor hexadecimal* | .NET Core 3.0 |
| **app.config para .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valor decimal* | .NET Framework 4.6.2 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Especifica a lista de processadores a serem usados para segmentos coletores de lixo.
- Esta configuração é semelhante ao [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto que permite especificar mais de 64 processadores.
- Para sistemas operacionais Windows, prefixe o número do processador ou o intervalo com o grupo de [CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10,0:12,1:50-52,1:70".
- Se [a afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desativada, essa configuração será ignorada.
- Aplica-se apenas à coleta de lixo do servidor.
- Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.GCHeapAffinitizeRanges` | Lista separada por comma de números de processadores ou faixas de números de processadores.<br/>Exemplo unix: "1-10,12,50-52,70"<br/>Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeRanges` | Lista separada por comma de números de processadores ou faixas de números de processadores.<br/>Exemplo unix: "1-10,12,50-52,70"<br/>Exemplo do Windows: "0:1-10,0:12,1:50-52,1:70" | .NET Core 3.0 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a>COMPlus_GCCpuGroup

- Configura se o coletor de lixo usa ou não [grupos de CPU.](/windows/win32/procthread/processor-groups)

  Quando um computador Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, permitindo que esse elemento estenda a coleta de lixo em todos os grupos de CPU. O coletor de lixo usa todos os núcleos para criar e equilibrar pilhas.

- Aplica-se à coleta de lixo do servidor apenas em sistemas de operação Windows de 64 bits.
- Padrão: Desabilitado ( ).`0`
- Para obter mais informações, consulte [Tornando a configuração da CPU melhor para GC em máquinas com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog de Maoni Stephens.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCCpuGroup` | `0`- deficientes<br/>`1`- habilitado | .NET Core 1.0 |
| **app.config para .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`- deficientes<br/>`true`- habilitado |  |

> [!NOTE]
> Para configurar o tempo de execução de idioma comum (CLR) para também distribuir threads do pool de segmentos em todos os grupos da CPU, habilite a opção [de elemento Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) Para aplicativos .NET Core, você pode habilitar `COMPlus_Thread_UseAllCpuGroups` essa opção `1`definindo o valor da variável ambiente para .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System.GC.NoAffinitize/COMPlus_GCNoAffinitize

- Especifica se é *a adesão dos* segmentos de coleta de lixo com processadores. Adenar um segmento GC significa que ele só pode ser executado em sua CPU específica. Um monte é criado para cada segmento GC.
- Aplica-se apenas à coleta de lixo do servidor.
- Padrão: Afena os fios de coleta`false`de lixo com processadores ().

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.NoAffinitize` | `false`- afeição<br/>`true`- não afete | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCNoAffinitize` | `0`- afeição<br/>`1`- não afete | .NET Core 3.0 |
| **app.config para .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`- afeição<br/>`true`- não afete | .NET Framework 4.6.2 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit

- Especifica o tamanho máximo de confirmação, em bytes, para a contabilidade GC heap e GC.
- Esta configuração só se aplica a computadores de 64 bits.
- O valor padrão, que só se aplica em certos casos, é o menor de 20 MB ou 75% do limite de memória no recipiente. O valor padrão se aplica se:

  - O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.
  - [System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimit` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapHardLimit` | *valor hexadecimal* | .NET Core 3.0 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para especificar um limite rígido de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável ambiente.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Especifica o uso permitido do heap GC como uma porcentagem da memória física total.
- Se [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também estiver definido, essa configuração será ignorada.
- Esta configuração só se aplica a computadores de 64 bits.
- Se o processo estiver sendo executado dentro de um recipiente que tenha um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.
- O valor padrão, que só se aplica em certos casos, é o menor de 20 MB ou 75% do limite de memória no recipiente. O valor padrão se aplica se:

  - O processo está sendo executado dentro de um recipiente que tem um limite de memória especificado.
  - [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.HeapHardLimitPercent` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapHardLimitPercent` | *valor hexadecimal* | .NET Core 3.0 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o uso do heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável ambiente.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System.GC.RetainVM/COMPlus_GCRetainVM

- Configura se os segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (OS).
- Padrão: Liberar segmentos de`false`volta ao sistema operacional ( ).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.RetainVM` | `false`- lançamento para os SO<br/>`true`- colocar em espera | .NET Core 1.0 |
| **Propriedade MSBuild** | `RetainVMGarbageCollection` | `false`- lançamento para os SO<br/>`true`- colocar em espera | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_GCRetainVM` | `0`- lançamento para os SO<br/>`1`- colocar em espera | .NET Core 1.0 |

### <a name="examples"></a>Exemplos

*arquivo runtimeconfig.json:*

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Páginas grandes

### <a name="complus_gclargepages"></a>COMPlus_GCLargePages

- Especifica se páginas grandes devem ser usadas quando um limite rígido de pilha é definido.
- Padrão: Desabilitado ( ).`0`
- Este é um cenário experimental.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCLargePages` | `0`- deficientes<br/>`1`- habilitado | .NET Core 3.0 |

## <a name="large-objects"></a>Objetos grandes

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configura suporte a coletores de lixo em plataformas de 64 bits para arrays maiores que 2 gigabytes (GB) em tamanho total.
- Padrão: Ativado`1`().
- Essa opção pode se tornar obsoleta em uma versão futura do .NET.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_gcAllowVeryLargeObjects` | `1`- habilitado<br/> `0`- deficientes | .NET Core 1.0 |
| **app.config para .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`- habilitado<br/> `0`- deficientes | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Grande limiar de pilha de objetos

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a>System.GC.LOHThreshold/COMPlus_GCLOHThreshold

- Especifica o tamanho do limiar, em bytes, que faz com que os objetos vão para o heap de objeto grande (LOH).
- O limite padrão é de 85.000 bytes.
- O valor especificado deve ser maior do que o limite padrão.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | `System.GC.LOHThreshold` | *valor decimal* | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_GCLOHThreshold` | *valor hexadecimal* | .NET Core 1.0 |
| **app.config para .NET Framework** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *valor decimal* | .NET Framework 4.8 |

Exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> Se estiver definindo a opção em *runtimeconfig.json,* especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável ambiente.

## <a name="standalone-gc"></a>GC autônomo

### <a name="complus_gcname"></a>COMPlus_GCName

- Especifica um caminho para a biblioteca contendo o coletor de lixo que o tempo de execução pretende carregar.
- Para obter mais informações, consulte [o design do carregador GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig.json** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
