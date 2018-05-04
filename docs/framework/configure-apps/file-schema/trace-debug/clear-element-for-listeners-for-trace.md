---
title: '&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1705ed7cc847d60ecf8b42f4615d77f2cc569e21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Limpar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;
Limpa a coleção `Listeners` do rastreamento.  
  
 \<configuration>  
\<System. Diagnostics >  
\<rastreamento >  
\<ouvintes >  
\<Limpar >  
  
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
|`listeners`|Contém os ouvintes que coletarem, armazenam e rotear mensagens. Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.|  
  
## <a name="remarks"></a>Comentários  
 O `<clear>` elemento remove todos os ouvintes do `Listeners` coleta de rastreamento. Você pode usar o `<clear>` elemento antes de usar o `<add>` elemento para ter certeza de que não há nenhum outros ouvintes ativos na coleção.  
  
 Você pode limpar o `Listeners` coleção programaticamente, chamando o <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> método no <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriedade (`System.Diagnostics.Trace.Listeners.Clear()`).  
  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
> [!NOTE]
>  O `<clear>` elemento remove o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção, alterando o comportamento do <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos. Chamando um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem. No entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<clear>` elemento antes de usar o `<add>` elemento para adicionar o ouvinte `console` para o `Listeners` coleta de rastreamento.  
  
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
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
