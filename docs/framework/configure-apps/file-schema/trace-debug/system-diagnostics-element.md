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
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699191"
---
# <a name="systemdiagnostics-element"></a>\<elemento > System. Diagnostics
Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. diagnostics >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
 None.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.|  
|[\<performanceCounters>](performancecounters-element.md)|Especifica o tamanho da memória global compartilhada por contadores de desempenho.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento. Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.|  
|[\<sources>](sources-element.md)|Especifica fontes de rastreamento que iniciam mensagens de rastreamento.|  
|[\<switches>](switches-element.md)|Contém opções de rastreamento e os níveis em que as opções de rastreamento são definidas.|  
|[\<trace>](trace-element.md)|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir mostra como inserir uma opção de rastreamento e um ouvinte de rastreamento dentro do elemento **\<System. diagnostics >** . A opção de rastreamento de `General` é definida como o nível de <xref:System.Diagnostics.TraceLevel>. O ouvinte de rastreamento `myListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo.  
  
> [!NOTE]
> No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção. Por exemplo, você pode especificar `true` para um <xref:System.Diagnostics.BooleanSwitch> ou usar o texto que representa um valor de enumeração, como `Error` para um <xref:System.Diagnostics.TraceSwitch>. A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.  
  
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
