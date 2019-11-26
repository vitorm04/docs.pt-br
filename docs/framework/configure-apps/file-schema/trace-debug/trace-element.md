---
title: Elemento <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699176"
---
# <a name="trace-element"></a>Elemento de > de rastreamento de \<
Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. Diagnostics >** ](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<trace >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`autoflush`|Atributo opcional.<br /><br /> Especifica se os ouvintes de rastreamento liberam automaticamente o buffer de saída após cada operação de gravação.|  
|`indentsize`|Atributo opcional.<br /><br /> Especifica o número de espaços a serem recuados.|  
|`useGlobalLock`|Atributo opcional.<br /><br /> Indica se o bloqueio global deve ser usado.|  
  
## <a name="autoflush-attribute"></a>Atributo autoflush  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não libera automaticamente o buffer de saída. Esse é o padrão.|  
|`true`|Libera automaticamente o buffer de saída.|  
  
## <a name="usegloballock-attribute"></a>Atributo useGlobalLock  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não usará o bloqueio global se o ouvinte for thread-safe; caso contrário, o usará o bloqueio global.|  
|`true`|Usa o bloqueio global independentemente de o ouvinte ser thread-safe. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|Especifica um ouvinte que coleta, armazena e roteia mensagens.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir mostra como usar o elemento `<trace>` para adicionar o ouvinte `MyListener` à coleção de `Listeners`. `MyListener` cria um arquivo chamado `MyListener.log` e grava a saída no arquivo. O atributo `useGlobalLock` é definido como `false`, o que faz com que o bloqueio global não seja usado se o ouvinte de rastreamento for thread-safe. O atributo `autoflush` é definido como `true`, o que faz com que o ouvinte de rastreamento grave no arquivo, independentemente de o método <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> ser chamado. O atributo `indentsize` é definido como 0 (zero), o que faz com que o ouvinte recue zero espaços quando o método <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> é chamado.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
