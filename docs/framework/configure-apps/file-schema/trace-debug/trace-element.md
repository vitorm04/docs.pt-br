---
title: '&lt;rastreamento&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d7ddcbdbdbbc2924d4f725d2fd401f873a4cfb0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttracegt-element"></a>&lt;rastreamento&gt; elemento
Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.  
  
 \<configuration>  
\<System. Diagnostics >  
\<rastreamento >  
  
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
|`autoflush`|Atributo opcional.<br /><br /> Especifica se os ouvintes de rastreamento automaticamente liberar o buffer de saída depois de cada operação de gravação.|  
|`indentsize`|Atributo opcional.<br /><br /> Especifica o número de espaços para recuar.|  
|`useGlobalLock`|Atributo opcional.<br /><br /> Indica se o bloqueio global deve ser usado.|  
  
## <a name="autoflush-attribute"></a>autoflush atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não limpa automaticamente o buffer de saída. Esse é o padrão.|  
|`true`|Automaticamente libera o buffer de saída.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não use o bloqueio global se o ouvinte é thread-safe; Caso contrário, usará o bloqueio global.|  
|`true`|Usa o bloqueio global, independentemente se o ouvinte é thread-safe. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Especifica um ouvinte que coleta, armazena e roteamento de mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<trace>` elemento para adicionar o ouvinte `MyListener` para o `Listeners` coleção. `MyListener`cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo. O `useGlobalLock` atributo é definido como `false`, que faz com que o bloqueio global não deve ser usado se o ouvinte de rastreamento é thread-safe. O `autoflush` atributo é definido como `true`, que faz com que o ouvinte de rastreamento gravar o arquivo independentemente se o <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> método é chamado. O `indentsize` atributo é definido como 0 (zero), que faz com que o ouvinte recuar os espaços de zero quando o <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> método é chamado.  
  
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
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
