---
title: '&lt;remover&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 11f4b648ac1ffc614f18a3686eb2b6508a272980
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;remover&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;
Remove um ouvinte do **ouvintes** coleção.  
  
 \<configuration>  
\<System. Diagnostics >  
\<rastreamento >  
\<ouvintes >  
\<remove>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**name**|Atributo obrigatório.<br /><br /> O nome do ouvinte a remova o **ouvintes** coleção.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`listeners`|Especifica um ouvinte que coleta, armazena e roteamento de mensagens. Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`trace`|Configura o serviço de rastreamento do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Removendo o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção altera o comportamento do <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos. Chamando um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão do rastreamento **ouvintes** coleção.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
