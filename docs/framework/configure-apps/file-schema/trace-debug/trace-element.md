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
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153160"
---
# <a name="trace-element"></a>\<traço> Elemento
Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<traçar>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`autoflush`|Atributo opcional.<br /><br /> Especifica se os ouvintes de rastreamento liberam automaticamente o buffer de saída após cada operação de gravação.|  
|`indentsize`|Atributo opcional.<br /><br /> Especifica o número de espaços a serem recuados.|  
|`useGlobalLock`|Atributo opcional.<br /><br /> Indica se o bloqueio global deve ser usado.|  
  
## <a name="autoflush-attribute"></a>Atributo de descarga automática  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não libera automaticamente o buffer de saída. Esse é o padrão.|  
|`true`|Libera automaticamente o buffer de saída.|  
  
## <a name="usegloballock-attribute"></a>useAtributoGlobalLock  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não usa o bloqueio global se o ouvinte estiver seguro para rosca; caso contrário, usa o bloqueio global.|  
|`true`|Usa o bloqueio global independentemente de o ouvinte estar seguro para o segmento. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<ouvintes>](listeners-element-for-trace.md)|Especifica um ouvinte que coleta, armazena e encaminha mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<trace>` mostra como usar `MyListener` o `Listeners` elemento para adicionar o ouvinte à coleção. `MyListener`cria um arquivo `MyListener.log` que é nomeado e grava a saída para o arquivo. O `useGlobalLock` atributo `false`é definido como , o que faz com que o bloqueio global não seja usado se o ouvinte de rastreamento estiver seguro para rosca. O `autoflush` atributo `true`é definido como , o que faz com <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> que o ouvinte de rastreamento escreva para o arquivo, independentemente de o método ser chamado. O `indentsize` atributo é definido como 0 (zero), o que <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> faz com que o ouvinte recue zero espaços quando o método é chamado.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
