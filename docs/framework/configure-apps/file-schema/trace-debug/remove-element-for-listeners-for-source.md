---
title: <remove> Elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4809c471deb51e0560b438b5a2c8849daad34ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120127"
---
# <a name="remove-element-for-listeners-for-source"></a>\<Remover > elemento para \<ouvintes > para \<origem >
Remove um ouvinte da coleção `Listeners` de uma origem de rastreamento.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<origem >  
\<listeners>  
\<remove>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo obrigatório.<br /><br /> O nome do ouvinte para remover o `Listeners` coleção.|  
  
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
 O `<remove>` elemento remove um ouvinte especificado do `Listeners` coleção para uma origem de rastreamento.  
  
 Você pode remover um elemento a `Listeners` coleção para uma origem de rastreamento programaticamente, chamando o <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> método na <xref:System.Diagnostics.TraceSource.Listeners%2A> propriedade do <xref:System.Diagnostics.TraceSource> instância.  
  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<remove>` elemento antes de usar o `<add>` elemento para adicionar o ouvinte `console` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`.  
  
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
- [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
