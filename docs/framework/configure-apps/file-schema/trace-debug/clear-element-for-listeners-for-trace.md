---
title: <clear> elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088923"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<limpar > elemento para \<ouvintes > para \<rastreamento >
Limpa a coleção `Listeners` do rastreamento.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes >** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
|`listeners`|Contém ouvintes que coletam, armazenam e roteiam mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<clear>` remove todos os ouvintes da coleção de `Listeners` para o rastreamento. Você pode usar o elemento `<clear>` antes de usar o elemento `<add>` para ter certeza de que não há outros ouvintes ativos na coleção.  
  
 Você pode limpar a coleção de `Listeners` programaticamente chamando o método <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na propriedade <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
> [!NOTE]
> O elemento `<clear>` remove o <xref:System.Diagnostics.DefaultTraceListener> da coleção de `Listeners`, alterando o comportamento dos métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. Chamar um método `Assert` ou `Fail` normalmente resulta na exibição de uma caixa de mensagem. No entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não estiver na coleção de `Listeners`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o elemento `<clear>` antes de usar o elemento `<add>` para adicionar o `console` do ouvinte à coleção de `Listeners` para rastreamento.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
