---
title: <remove>Elemento para <listeners> para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920485"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<remover o elemento > \<para ouvintes > \<para rastreamento >
Remove um ouvinte da coleção Listeners.  
  
 \<configuration>  
\<System. Diagnostics >  
\<> de rastreamento  
\<listeners>  
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
|**name**|Atributo obrigatório.<br /><br /> O nome do ouvinte a ser removido da coleção de ouvintes.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`listeners`|Especifica um ouvinte que coleta, armazena e roteia mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`trace`|Configura o serviço de rastreamento do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Remover o <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>da coleção altera o<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>comportamento dos métodos,, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. `Listeners` Chamar um `Assert` método `Fail` ou normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não <xref:System.Diagnostics.DefaultTraceListener> será exibida se `Listeners` o não estiver na coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como remover o ouvinte de rastreamento padrão da coleção de ouvintes de rastreamento.  
  
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

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
