---
title: '&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bbba1c805c6b300f7cf7b3d9112cde9df7607a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a>&lt;filtro&gt; elemento para &lt;adicionar&gt; para &lt;sharedListeners&gt;
Adiciona um filtro a um ouvinte na coleção `sharedListeners`.  
  
 \<configuration>  
\<System. Diagnostics >  
\<sharedListeners > elemento  
\<add>  
\<Filtro >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**type**|Atributo obrigatório.<br /><br /> Especifica o tipo do filtro. Você pode usar apenas o nome completo do tipo (no formato do <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade), ou você pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly (no formato de <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> propriedade). Para obter informações sobre a criação de um nome de tipo totalmente qualificado, consulte [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sharedListeners`|Uma coleção de ouvintes que podem referenciar qualquer origem ou o elemento de rastreamento.|  
|`add`|Adiciona um ouvinte para o **sharedListeners** coleção.|  
  
## <a name="remarks"></a>Comentários  
 Se um ouvinte é definido em um `<add>` elemento do `<sharedListeners>` elemento, o filtro para esse ouvinte deve ser definido em um `<filter>` que é um filho do elemento de `<add>` elemento.  
  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<filter>` elemento para adicionar um filtro para o ouvinte de rastreamento `console` no `sharedListeners` coleção.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
