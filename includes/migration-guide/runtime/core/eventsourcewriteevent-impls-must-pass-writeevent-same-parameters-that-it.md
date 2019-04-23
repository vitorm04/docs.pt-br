---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235033"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent deve passar a WriteEvent os mesmos parâmetros que recebeu (mais ID)

|   |   |
|---|---|
|Detalhes|O tempo de execução agora aplica o contrato que especifica o seguinte: Uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> que define um método de evento ETW deve chamar o método de classe base <code>EventSource.WriteEvent</code> com a ID do evento seguido dos mesmos argumentos que o método de evento ETW passou.|
|Sugestão|Uma exceção <xref:System.IndexOutOfRangeException?displayProperty=name> será acionada se um <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> ler dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> no processo de uma origem de evento que viola esse contrato.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|
