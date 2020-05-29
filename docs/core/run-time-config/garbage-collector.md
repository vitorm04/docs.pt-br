---
title: Definições de configuração do coletor de lixo
description: Saiba mais sobre as configurações de tempo de execução para configurar como o coletor de lixo gerencia a memória para aplicativos .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 0ce2f70204463c1525ef7d29de21ddf5384d0238
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202095"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Opções de configuração de tempo de execução para coleta de lixo

Esta página contém informações sobre as configurações de coletor de lixo (GC) que podem ser alteradas em tempo de execução. Se você estiver tentando atingir o desempenho máximo de um aplicativo em execução, considere o uso dessas configurações. No entanto, os padrões fornecem um desempenho ideal para a maioria dos aplicativos em situações típicas.

As configurações são organizadas em grupos nesta página. As configurações em cada grupo são comumente usadas em conjunto entre si para obter um resultado específico.

> [!NOTE]
>
> - Essas configurações também podem ser alteradas dinamicamente pelo aplicativo enquanto ele está em execução, portanto, as configurações de tempo de execução definidas podem ser substituídas.
> - Algumas configurações, como [nível de latência](../../standard/garbage-collection/latency.md), normalmente são definidas somente por meio da API em tempo de design. Essas configurações são omitidas desta página.
> - Para valores numéricos, use a notação decimal para as configurações no arquivo *runtimeconfig. JSON* e notação hexadecimal para configurações de variável de ambiente. Para valores hexadecimais, você pode especificá-los com ou sem o prefixo "0x".

## <a name="flavors-of-garbage-collection"></a>Tipos de coleta de lixo

Os dois tipos principais de coleta de lixo são estação de trabalho GC e GC de servidor. Para obter mais informações sobre as diferenças entre as duas, consulte [estação de trabalho e coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).

Os subtipos de coleta de lixo são em segundo plano e não simultâneos.

Use as seguintes configurações para selecionar tipos de coleta de lixo:

### <a name="systemgcservercomplus_gcserver"></a>System. GC. Server/COMPlus_gcServer

- Define se o aplicativo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor.
- Padrão: coleta de lixo da estação de trabalho. Isso é equivalente a definir o valor como `false` .

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Server` | `false`-Estação de trabalho<br/>`true`-servidor | .NET Core 1.0 |
| **Propriedade do MSBuild** | `ServerGarbageCollection` | `false`-Estação de trabalho<br/>`true`-servidor | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcServer` | `0`-Estação de trabalho<br/>`1`-servidor | .NET Core 1.0 |
| **App. config para .NET Framework** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false`-Estação de trabalho<br/>`true`-servidor |  |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

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

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a>System. GC. simultaneamente/COMPlus_gcConcurrent

- Configura se a coleta de lixo em segundo plano (simultânea) está habilitada.
- Padrão: usar GC em segundo plano. Isso é equivalente a definir o valor como `true` .
- Para obter mais informações, consulte [coleta de lixo em segundo plano](../../standard/garbage-collection/background-gc.md).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.Concurrent` | `true`-GC em segundo plano<br/>`false`-GC não simultâneo | .NET Core 1.0 |
| **Propriedade do MSBuild** | `ConcurrentGarbageCollection` | `true`-GC em segundo plano<br/>`false`-GC não simultâneo | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_gcConcurrent` | `1`-GC em segundo plano<br/>`0`-GC não simultâneo | .NET Core 1.0 |
| **App. config para .NET Framework** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true`-GC em segundo plano<br/>`false`-GC não simultâneo |  |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

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

Use as configurações descritas nesta seção para gerenciar a memória e o uso do processador do coletor de lixo.

Para obter mais informações sobre algumas dessas configurações, consulte o meio-termo entre a entrada de blog do [GC de estação de trabalho e servidor](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .

### <a name="systemgcheapcountcomplus_gcheapcount"></a>System. GC. HeapCount/COMPlus_GCHeapCount

- Limita o número de heaps criados pelo coletor de lixo.
- Aplica-se somente à coleta de lixo do servidor.
- Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver habilitada, que é o padrão, a configuração de contagem de heap affinitizes `n` heaps/threads do GC para os primeiros `n` processadores. (Use a [máscara relacionar](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) ou as configurações de [intervalos de relacionar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) para especificar exatamente quais processadores relacionar.)
- Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração limitará o número de heaps do GC.
- Para obter mais informações, consulte o [GCHeapCount comentários](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapCount` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapCount` | *valor hexadecimal* | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *valor decimal* | .NET Framework 4.6.2 |

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
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o número de heaps a 16, os valores seriam 16 para o arquivo JSON e 0x10 ou 10 para a variável de ambiente.

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a>System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask

- Especifica os processadores exatos que os threads do coletor de lixo devem usar.
- Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.
- Aplica-se somente à coleta de lixo do servidor.
- O valor é uma máscara de bits que define os processadores que estão disponíveis para o processo. Por exemplo, um valor decimal de 1023 (ou um valor hexadecimal de 0x3FF ou 3FF se você estiver usando a variável de ambiente) é 0011 1111 1111 em notação binária. Isso especifica que os primeiros 10 processadores devem ser usados. Para especificar os 10 próximos processadores, ou seja, os processadores 10-19, especifique um valor decimal de 1047552 (ou um valor hexadecimal de 0xFFC00 ou FFC00), que é equivalente a um valor binário de 1111 1111 1100 0000 0000.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapAffinitizeMask` | *valor decimal* | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeMask` | *valor hexadecimal* | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *valor decimal* | .NET Framework 4.6.2 |

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

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a>System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges

- Especifica a lista de processadores a serem usados para threads do coletor de lixo.
- Essa configuração é semelhante a [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), exceto pelo fato de que ela permite que você especifique mais de 64 processadores.
- Para sistemas operacionais Windows, Prefixe o número do processador ou o intervalo com o [grupo de CPU](/windows/win32/procthread/processor-groups)correspondente, por exemplo, "0:1-10, 0:12, 1:50-52, 1:70".
- Se a [afinidade do processador GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) estiver desabilitada, essa configuração será ignorada.
- Aplica-se somente à coleta de lixo do servidor.
- Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.GCHeapAffinitizeRanges` | Lista separada por vírgulas de números de processador ou intervalos de números de processador.<br/>Exemplo de UNIX: "1-10, 12, 50-52, 70"<br/>Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCHeapAffinitizeRanges` | Lista separada por vírgulas de números de processador ou intervalos de números de processador.<br/>Exemplo de UNIX: "1-10, 12, 50-52, 70"<br/>Exemplo do Windows: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

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

- Configura se o coletor de lixo usa [grupos de CPU](/windows/win32/procthread/processor-groups) ou não.

  Quando um computador com Windows de 64 bits tem vários grupos de CPU, ou seja, há mais de 64 processadores, a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU. O coletor de lixo usa todos os núcleos para criar e balancear heaps.

- Aplica-se à coleta de lixo do servidor somente em sistemas de operação do Windows de 64 bits.
- Padrão: o GC não se estende por grupos de CPU. Isso é equivalente a definir o valor como `0` .
- Para obter mais informações, consulte [tornando a configuração de CPU melhor para GC em computadores com > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) no blog do Maoni Stephens '.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCCpuGroup` | `0`-desabilitado<br/>`1`-habilitado | .NET Core 1.0 |
| **App. config para .NET Framework** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false`-desabilitado<br/>`true`-habilitado |  |

> [!NOTE]
> Para configurar o Common Language Runtime (CLR) para também distribuir threads do pool de threads em todos os grupos de CPU, habilite a opção de [elemento Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) . Para aplicativos .NET Core, você pode habilitar essa opção definindo o valor da variável de `COMPlus_Thread_UseAllCpuGroups` ambiente como `1` .

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a>System. GC. NoAffinitize/COMPlus_GCNoAffinitize

- Especifica se os threads de coleta de lixo devem ser *relacionardos* com processadores. Para relacionar um thread de GC significa que ele só pode ser executado em sua CPU específica. Um heap é criado para cada thread do GC.
- Aplica-se somente à coleta de lixo do servidor.
- Padrão: relacionar os threads de coleta de lixo com processadores. Isso é equivalente a definir o valor como `false` .

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.NoAffinitize` | `false`-relacionar<br/>`true`-Não relacionar | .NET Core 3.0 |
| **Variável de ambiente** | `COMPlus_GCNoAffinitize` | `0`-relacionar<br/>`1`-Não relacionar | .NET Core 3.0 |
| **App. config para .NET Framework** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false`-relacionar<br/>`true`-Não relacionar | .NET Framework 4.6.2 |

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

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a>System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit

- Especifica o tamanho máximo de confirmação, em bytes, para o heap de GC e a escrituração de GC.
- Essa configuração se aplica somente a computadores de 64 bits.
- O valor padrão, que se aplica apenas em determinados casos, é o maior de 20 MB ou 75% do limite de memória no contêiner. O valor padrão se aplica se:

  - O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.
  - [System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) não está definido.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimit` | *valor decimal* | .NET Core 3.0 |
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
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para especificar um limite rígido de heap de 200 mebibytes (MiB), os valores seriam 209715200 para o arquivo JSON e 0xC800000 ou C800000 para a variável de ambiente.

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a>System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent

- Especifica o uso de heap de GC permitido como uma porcentagem da memória física total.
- Se [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) também for definido, essa configuração será ignorada.
- Essa configuração se aplica somente a computadores de 64 bits.
- Se o processo estiver sendo executado dentro de um contêiner que tem um limite de memória especificado, a porcentagem será calculada como uma porcentagem desse limite de memória.
- O valor padrão, que se aplica apenas em determinados casos, é o menor de 20 MB ou 75% do limite de memória no contêiner. O valor padrão se aplica se:

  - O processo está sendo executado dentro de um contêiner que tem um limite de memória especificado.
  - [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) não está definido.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.HeapHardLimitPercent` | *valor decimal* | .NET Core 3.0 |
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
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para limitar o uso de heap a 30%, os valores seriam 30 para o arquivo JSON e 0x1E ou 1E para a variável de ambiente.

### <a name="systemgcretainvmcomplus_gcretainvm"></a>System. GC. RetainVM/COMPlus_GCRetainVM

- Configura se OS segmentos que devem ser excluídos são colocados em uma lista de espera para uso futuro ou são liberados de volta para o sistema operacional (SO).
- Padrão: libera segmentos de volta para o sistema operacional. Isso é equivalente a definir o valor como `false` .

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.GC.RetainVM` | `false`-versão para o sistema operacional<br/>`true`-colocar em espera | .NET Core 1.0 |
| **Propriedade do MSBuild** | `RetainVMGarbageCollection` | `false`-versão para o sistema operacional<br/>`true`-colocar em espera | .NET Core 1.0 |
| **Variável de ambiente** | `COMPlus_GCRetainVM` | `0`-versão para o sistema operacional<br/>`1`-colocar em espera | .NET Core 1.0 |

### <a name="examples"></a>Exemplos

arquivo *runtimeconfig. JSON* :

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

- Especifica se páginas grandes devem ser usadas quando um limite rígido de heap for definido.
- Padrão: não use páginas grandes quando um limite rígido de heap for definido. Isso é equivalente a definir o valor como `0` .
- Essa é uma configuração experimental.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCLargePages` | `0`-desabilitado<br/>`1`-habilitado | .NET Core 3.0 |

## <a name="large-objects"></a>Objetos grandes

### <a name="complus_gcallowverylargeobjects"></a>COMPlus_gcAllowVeryLargeObjects

- Configura o suporte ao coletor de lixo em plataformas de 64 bits para matrizes com mais de 2 gigabytes (GB) no tamanho total.
- Padrão: o GC dá suporte a matrizes maiores que 2 GB. Isso é equivalente a definir o valor como `1` .
- Essa opção pode se tornar obsoleta em uma versão futura do .NET.

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_gcAllowVeryLargeObjects` | `1`-habilitado<br/> `0`-desabilitado | .NET Core 1.0 |
| **App. config para .NET Framework** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1`-habilitado<br/> `0`-desabilitado | .NET Framework 4.5 |

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
> Se você estiver definindo a opção em *runtimeconfig. JSON*, especifique um valor decimal. Se você estiver definindo a opção como uma variável de ambiente, especifique um valor hexadecimal. Por exemplo, para definir um tamanho de limite de 120.000 bytes, os valores seriam 120000 para o arquivo JSON e 0x1D4C0 ou 1D4C0 para a variável de ambiente.

## <a name="standalone-gc"></a>GC autônomo

### <a name="complus_gcname"></a>COMPlus_GCName

- Especifica um caminho para a biblioteca que contém o coletor de lixo que o tempo de execução pretende carregar.
- Para obter mais informações, consulte [design de carregador de GC autônomo](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).

| | Nome da configuração | Valores | Versão introduzida |
| - | - | - | - |
| **runtimeconfig. JSON** | N/D | N/D | N/D |
| **Variável de ambiente** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
