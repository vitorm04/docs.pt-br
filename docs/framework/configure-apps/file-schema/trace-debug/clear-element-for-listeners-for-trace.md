---
title: <clear>Elemento <listeners> para para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153536"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<elemento> \<claro para \<os ouvintes> para> de rastreamento
Limpa a coleção `Listeners` do rastreamento.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<traçar>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claro>**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
|`listeners`|Contém ouvintes que coletam, armazenam e encaminham mensagens. Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.|  
  
## <a name="remarks"></a>Comentários  
 O `<clear>` elemento remove todos `Listeners` os ouvintes da coleção para rastreamento. Você pode `<clear>` usar o `<add>` elemento antes de usar o elemento para ter certeza de que não há outros ouvintes ativos na coleção.  
  
 Você pode `Listeners` limpar a coleção de <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> forma <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> programática`System.Diagnostics.Trace.Listeners.Clear()`ligando para o método na propriedade ( ).  
  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.  
  
> [!NOTE]
> O `<clear>` elemento remove <xref:System.Diagnostics.DefaultTraceListener> o `Listeners` da coleção, alterando <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>o <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>comportamento <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> dos métodos e métodos. Chamar `Assert` um `Fail` ou método normalmente resulta na exibição de uma caixa de mensagem. No entanto, a caixa de <xref:System.Diagnostics.DefaultTraceListener> mensagem `Listeners` não é exibida se a não estiver na coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<clear>` mostra como `<add>` usar o elemento `console` antes `Listeners` de usar o elemento para adicionar o ouvinte à coleção para rastreamento.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [\<remover>](remove-element-for-listeners-for-trace.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
