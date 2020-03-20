---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858611"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>EventListeners do ETW não capturam eventos dos provedores com palavras-chave explícitas (como o provedor TPL)

|   |   |
|---|---|
|Detalhes|EventListeners do ETW com uma máscara de palavra-chave em branco não capturam eventos corretamente dos provedores com palavras-chave explícitas. No .NET Framework 4.5, o provedor TPL começou a fornecer palavras-chave explícitas e disparou esse problema. No .NET Framework 4.6, EventListeners foram atualizados para não apresentarem mais esse problema.|
|Sugestão|Para contornar esse problema, substitua as chamadas para <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> com chamadas para a sobrecarga EnableEvents que especifica explicitamente a máscara &quot;quaisquer palavras-chave&quot; a ser usada: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
