---
title: <clear>Elemento para <listeners> para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927177"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<limpar > elemento para \<ouvintes > para \<rastreamento >
Limpa a coleção `Listeners` do rastreamento.  
  
 \<configuration>  
\<System. Diagnostics >  
\<> de rastreamento  
\<listeners>  
\<clear>  
  
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
 O `<clear>` elemento remove todos os ouvintes `Listeners` da coleção para rastreamento. Você pode usar o `<clear>` elemento antes de usar `<add>` o elemento para ter certeza de que não há outros ouvintes ativos na coleção.  
  
 Você pode limpar a `Listeners` coleção programaticamente chamando <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> o método na <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> Propriedade (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
> [!NOTE]
> O `<clear>` elemento remove o <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>da `Listeners` <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> coleção,<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> alterando o comportamento dos métodos ,,e.<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Chamar um `Assert` método `Fail` ou normalmente resulta na exibição de uma caixa de mensagem. No entanto, a caixa de mensagem não será <xref:System.Diagnostics.DefaultTraceListener> exibida se o não `Listeners` estiver na coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar `<add>` o elemento para `Listeners` adicionar o `console` ouvinte à coleção para rastreamento.  
  
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
