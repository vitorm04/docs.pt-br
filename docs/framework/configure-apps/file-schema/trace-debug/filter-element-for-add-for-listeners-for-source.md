---
title: <filter> elemento para <add> para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 766088b8a26ce3218031df74b193658ba8024280
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088904"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filtrar o elemento > para \<Adicionar > para os ouvintes \<> para \<fonte >
Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**fontes**](sources-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**fonte >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes**](listeners-element-for-source.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<adicionar >** ](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**filtro >**

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
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo do filtro, que deve herdar da classe <xref:System.Diagnostics.TraceFilter>. Você pode usar o nome qualificado de namespace do tipo, que corresponde à propriedade de <xref:System.Type.FullName%2A> do tipo, ou pode usar o nome de tipo totalmente qualificado, incluindo as informações de assembly, que correspondem à propriedade <xref:System.Type.AssemblyQualifiedName%2A>. Para obter informações sobre nomes de tipo totalmente qualificados, consulte [especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor da classe de filtro especificada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Contém ouvintes que coletam, armazenam e roteiam mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
|`add`|Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<filter>` deve estar contido em um elemento `<add>` para um ouvinte de origem de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [> de sharedListeners\<](sharedlisteners-element.md). Se o ouvinte for definido em uma [\<sharedListeners](sharedlisteners-element.md), o filtro desse ouvinte deverá ser definido nesse elemento.  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `<filter>` para adicionar um filtro ao ouvinte `console` na coleção de `Listeners` para a origem de rastreamento `myTraceSource`, especificando o nível de evento de filtro como `Error`.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Esquema de configurações de rastreamento e depuração](index.md)
