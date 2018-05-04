---
title: '&lt;ouvintes de&gt; elemento para &lt;rastreamento&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2f0d795d6a8789772ff3fd46648fbc0d683c66e5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltlistenersgt-element-for-lttracegt"></a>&lt;ouvintes de&gt; elemento para &lt;rastreamento&gt;
Especifica um ouvinte que coleta, armazena e roteamento de mensagens. Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.  
  
 \<Configuração > elemento  
\<System. Diagnostics > elemento  
\<rastreamento > elemento  
\<ouvintes > elemento \<rastreamento >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Adiciona um ouvinte na coleção `Listeners`.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Limpa a coleção `Listeners` do rastreamento.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Remove um ouvinte do `Listeners` coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes compartilham o mesmo **ouvintes** coleção. Se você adicionar um objeto de ouvinte para a coleção em uma dessas classes, de outra classe usa o mesmo ouvinte. As classes de ouvinte fornecidas com o .NET Framework derivam de <xref:System.Diagnostics.TraceListener> classe.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<ouvintes >** elemento para adicionar os ouvintes `MyListener` e `MyEventListener` para o **ouvintes** coleção. `MyListener` cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo. `MyEventListener` cria uma entrada no log de eventos.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.TraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
