---
title: Elemento <remove> para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 5a6b94756cb1b451d40229674dd887dd9f84676b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267060"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<Remover > elemento para \<ouvintes > para \<rastreamento >
Remove um ouvinte dos **ouvintes** coleção.  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
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
|**name**|Atributo obrigatório.<br /><br /> O nome do ouvinte para remover o **ouvintes** coleção.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`listeners`|Especifica um ouvinte que coleta, armazena e encaminha mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`trace`|Configura o serviço de rastreamento do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Removendo o <xref:System.Diagnostics.DefaultTraceListener> do `Listeners` coleção altera o comportamento das <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> métodos. Chamar um `Assert` ou `Fail` método normalmente resulta na exibição de uma caixa de mensagem, no entanto, a caixa de mensagem não será exibida se o <xref:System.Diagnostics.DefaultTraceListener> não está no `Listeners` coleção.  
  
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
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
