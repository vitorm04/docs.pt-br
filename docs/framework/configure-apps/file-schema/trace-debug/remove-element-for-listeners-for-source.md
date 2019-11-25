---
title: <remove> elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 75db45d4e868ce88e030ec6a43c8bdaf788a1102
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088849"
---
# <a name="remove-element-for-listeners-for-source"></a>\<remover > elemento para \<ouvintes > para \<fonte >
Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**fontes**](sources-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**fonte >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes**](listeners-element-for-source.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo obrigatório.<br /><br /> O nome do ouvinte a ser removido da coleção de `Listeners`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Especifica os ouvintes que coletam, armazenam e roteiam mensagens.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<remove>` remove um ouvinte especificado da coleção `Listeners` para uma origem de rastreamento.  
  
 Você pode remover um elemento da coleção de `Listeners` para uma fonte de rastreamento programaticamente chamando o método <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> na propriedade <xref:System.Diagnostics.TraceSource.Listeners%2A> da instância de <xref:System.Diagnostics.TraceSource>.  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `<remove>` antes de usar o elemento `<add>` para adicionar o `console` do ouvinte à coleção de `Listeners` para a fonte de rastreamento `TraceSourceApp`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
