---
title: Elemento <sharedListeners>
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
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926979"
---
# <a name="sharedlisteners-element"></a>\<Elemento de > de sharedListeners
Contém os ouvintes que podem ser referenciados por qualquer elemento de origem ou de rastreamento.  Esses ouvintes não recebem nenhum rastreamento por padrão e não é possível recuperar esses ouvintes em tempo de execução. Os ouvintes identificados como ouvintes compartilhados podem ser adicionados a fontes ou rastreamentos por nome.  
  
 \<configuration>  
\<System. Diagnostics >  
\<sharedListeners>  
  
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
|[\<add>](add-element-for-listeners-for-trace.md)|Adiciona um ouvinte na coleção `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 A adição de um ouvinte à coleção de ouvintes compartilhados não o torna um ouvinte ativo. Ele ainda deve ser adicionado a uma origem de rastreamento ou a um rastreamento adicionando-o `Listeners` à coleção para esse elemento Trace. As classes de ouvinte no .NET Framework derivam <xref:System.Diagnostics.TraceListener> da classe.  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<sharedListeners>` elemento para adicionar o ouvinte `console` à `Listeners` coleção para <xref:System.Diagnostics.TraceSource> as classes e <xref:System.Diagnostics.Trace> . O ouvinte de rastreamento do console grava informações de rastreamento no console por <xref:System.Diagnostics.TraceSource> meio <xref:System.Diagnostics.Trace>de chamadas para o ou o.  
  
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
</configuration>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.TraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
