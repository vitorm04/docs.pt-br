---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235109"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>EventListeners do ETW não capturam eventos dos provedores com palavras-chave explícitas (como o provedor TPL)

|   |   |
|---|---|
|Detalhes|EventListeners do ETW com uma máscara de palavra-chave em branco não capturam eventos corretamente dos provedores com palavras-chave explícitas. No .NET Framework 4.5, o provedor TPL começou a fornecer palavras-chave explícitas e disparou esse problema. No .NET Framework 4.6, EventListeners foram atualizados para não apresentarem mais esse problema.|
|Sugestão|Para contornar esse problema, substitua as chamadas para <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> com chamadas para a sobrecarga EnableEvents que especifica explicitamente a máscara &quot;quaisquer palavras-chave&quot; a ser usada: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
