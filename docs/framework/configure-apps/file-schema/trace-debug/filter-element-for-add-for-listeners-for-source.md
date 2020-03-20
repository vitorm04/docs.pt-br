---
title: <filter>Elemento <add> para <listeners> para para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153510"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filtrar> \<Elemento \<para adicionar \<> para os ouvintes> para> de origem
Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>fonte**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de filtro**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo do filtro, que <xref:System.Diagnostics.TraceFilter> deve herdar da classe. Você pode usar o nome qualificado do tipo, que corresponde <xref:System.Type.FullName%2A> à propriedade do tipo, ou pode usar o nome do <xref:System.Type.AssemblyQualifiedName%2A> tipo totalmente qualificado, incluindo as informações de montagem, que correspondem à propriedade. Para obter informações sobre nomes de tipo totalmente qualificados, consulte [Especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A seqüência passou para o construtor para a classe de filtro especificada.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Contém ouvintes que coletam, armazenam e encaminham mensagens. Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.|  
|`add`|Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 O `<filter>` elemento deve ser `<add>` contido em um elemento para um ouvinte de origem de rastreamento que especifique o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [ \<>de ouvintes compartilhados ](sharedlisteners-element.md). Se o ouvinte for definido em um [ \<>de Ouvintes compartilhados, ](sharedlisteners-element.md)o filtro para esse ouvinte deve ser definido nesse elemento.  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<filter>` mostra como usar o elemento `console` para `Listeners` adicionar um `myTraceSource`filtro ao ouvinte na `Error`coleção para a origem do rastreamento, especificando o nível de evento do filtro como .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Esquema de configurações de rastreamento e depuração](index.md)
