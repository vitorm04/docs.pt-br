---
title: <filter> elemento para <add> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: cc970240ac07ad3ea72be50d1e9af452da638fa9
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088886"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<filtrar > elemento para \<Adicionar > para ouvintes \<> para \<> de rastreamento
Adiciona um filtro a um ouvinte na coleção de `Listeners` para um rastreamento.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes >** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<adicionar >** ](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtro >**

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
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
|`listeners`|Contém ouvintes que coletam, armazenam e roteiam mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
|`add`|Adiciona um ouvinte na coleção `Listeners`.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<filter>` deve estar contido em um elemento `<add>` para um ouvinte de rastreamento que especifica o tipo do ouvinte, não apenas o nome de um ouvinte definido em um [\<sharedListeners](sharedlisteners-element.md). Se o ouvinte for definido em uma [\<sharedListeners](sharedlisteners-element.md), o filtro desse ouvinte deverá ser definido nesse elemento.  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `<filter>` para adicionar um filtro ao ouvinte `console` na coleção de `Listeners` para rastreamento, especificando o nível de evento de filtro como `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [Esquema de configurações de rastreamento e depuração](index.md)
