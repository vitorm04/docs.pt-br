---
title: < elemento > System. Diagnostics
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926940"
---
# <a name="systemdiagnostics-element"></a>\<Elemento de > System. Diagnostics
Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.  
  
 \<configuration>  
\<System. Diagnostics >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.|  
|[\<performanceCounters>](performancecounters-element.md)|Especifica o tamanho da memória global compartilhada por contadores de desempenho.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento. Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.|  
|[\<sources>](sources-element.md)|Especifica fontes de rastreamento que iniciam mensagens de rastreamento.|  
|[\<switches>](switches-element.md)|Contém opções de rastreamento e os níveis em que as opções de rastreamento são definidas.|  
|[\<trace>](trace-element.md)|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como inserir uma opção de rastreamento e um ouvinte de rastreamento dentro do  **\<elemento System. Diagnostics >** . A `General` opção de rastreamento é definida para <xref:System.Diagnostics.TraceLevel> o nível. O ouvinte `myListener` de rastreamento cria um `MyListener.log` arquivo chamado e grava a saída no arquivo.  
  
> [!NOTE]
> No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção. Por exemplo, você pode especificar `true` para um <xref:System.Diagnostics.BooleanSwitch> ou usar o texto que representa `Error` um valor de enumeração, como <xref:System.Diagnostics.TraceSwitch>para um. A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [Esquema de configurações de rastreamento e depuração](index.md)
