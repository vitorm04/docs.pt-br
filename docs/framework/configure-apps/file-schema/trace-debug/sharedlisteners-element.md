---
title: '&lt;sharedListeners&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b312ea8180c464fb9f955e7d7079cac930c8bf05
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070130"
---
# <a name="ltsharedlistenersgt-element"></a>&lt;sharedListeners&gt; elemento
Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.  Esses ouvintes não recebem os rastreamentos por padrão, e não é possível recuperar esses ouvintes em tempo de execução. Ouvintes identificados como ouvintes compartilhados podem ser adicionados à fontes ou rastreamentos por nome.  
  
 \<configuration>  
\<System. Diagnostics >  
\<sharedListeners >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Adiciona um ouvinte na coleção `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 Adicionar um ouvinte à coleção de ouvintes compartilhados não o torna um ouvinte ativo. Ela ainda deve ser adicionada a uma origem de rastreamento ou um rastreamento adicionando-à `Listeners` coleção para esse elemento de rastreamento. As classes de ouvinte no .NET Framework derivam o <xref:System.Diagnostics.TraceListener> classe.  
  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<sharedListeners>` elemento para adicionar o ouvinte `console` para o `Listeners` coleção para ambos os <xref:System.Diagnostics.TraceSource> e <xref:System.Diagnostics.Trace> classes. O ouvinte de rastreamento do console grava informações de rastreamento no console por meio de chamadas para um <xref:System.Diagnostics.TraceSource> ou <xref:System.Diagnostics.Trace>.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.TraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
