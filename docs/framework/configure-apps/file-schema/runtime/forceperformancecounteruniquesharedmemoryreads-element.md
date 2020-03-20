---
title: Elemento <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154134"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forceDesempenhoContador-ExclusivoSCompartilhadoS>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Indica se o PerfCounter.dll usa a configuração de registro CategoryOptions para determinar se deve carregar dados de contador de desempenho da memória compartilhada ou da memória global específicas da categoria.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|PerfCounter.dll não usa a configuração de registro CategoriaOptions Este é o padrão.|  
|`true`|PerfCounter.dll usa a configuração de registro CategoriaOptions.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões do .NET Framework antes do .NET Framework 4, a versão do PerfCounter.dll que foi carregada correspondia ao tempo de execução que foi carregado no processo. Se um computador tivesse a versão 1.1 do .NET Framework e o .NET Framework 2.0 instalados, um aplicativo .NET Framework 1.1 carregaria a versão .NET Framework 1.1 do PerfCounter.dll. Começando pelo .NET Framework 4, a versão mais recente instalada do PerfCounter.dll está carregada. Isso significa que um aplicativo .NET Framework 1.1 carregará a versão .NET Framework 4 do PerfCounter.dll se o .NET Framework 4 estiver instalado no computador.  
  
 Começando com o .NET Framework 4, ao consumir contadores de desempenho, o PerfCounter.dll verifica a entrada de registro CategoriaOptions para cada provedor para determinar se ele deve ler a partir da memória compartilhada específica da categoria ou da memória compartilhada global. O .NET Framework 1.1 PerfCounter.dll não lê essa entrada de registro, porque não está ciente da memória compartilhada específica da categoria; ele sempre lê a partir da memória compartilhada global.  
  
 Para compatibilidade retroativa, o .NET Framework 4 PerfCounter.dll não verifica a entrada de registro CategoriaOps ao ser executado em um aplicativo .NET Framework 1.1. Ele simplesmente usa memória compartilhada global, assim como o .NET Framework 1.1 PerfCounter.dll. No entanto, você pode instruir o .NET Framework 4 PerfCounter.dll a verificar a configuração do registro ativando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.  
  
> [!NOTE]
> Ativar o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a memória compartilhada específica da categoria seja usada. A configuração `true` ativada para apenas causar perfCounter.dll para fazer referência à configuração de registro CategoriaOps. A configuração padrão para CategoryOptions é usar memória compartilhada específica da categoria; no entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.  
  
 A chave de registro que contém a configuração CategoriaOps é HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoriaNome\>\Desempenho. Por padrão, CategoryOptions é definida como 3, o que instrui perfCounter.dll a usar memória compartilhada específica da categoria. Se CategoryOptions estiver definida como 0, o PerfCounter.dll usará memória compartilhada global. Os dados de instância serão reutilizados somente se o nome da instância que está sendo criada for idêntico à instância que está sendo reutilizada. Todas as versões serão capazes de escrever para a categoria. Se CategoryOptions for definida como 1, a memória compartilhada global será usada, mas os dados de ocorrência podem ser reutilizados se o nome da categoria tiver o mesmo comprimento da categoria que está sendo reutilizada.  
  
 As configurações 0 e 1 podem levar a vazamentos de memória e o preenchimento da memória do contador de desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o PerfCounter.dll deve fazer referência à entrada do registro CategoryOptions para determinar se ele deve usar memória compartilhada específica da categoria.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
