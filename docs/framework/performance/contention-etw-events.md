---
title: Eventos ETW de contenção-.NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716129"
---
# <a name="contention-etw-events"></a>Eventos ETW de contenção

Eventos de contenção são acionados sempre que há contenção em bloqueios <xref:System.Threading.Monitor?displayProperty=nameWithType> ou bloqueios nativos usados pelo runtime. A contenção ocorre quando um thread aguarda um bloqueio, enquanto outro thread possui o bloqueio.

A tabela a seguir mostra a palavra-chave com a qual os eventos de contenção são acionados, além do nível dos eventos. Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).

|Palavra-chave para acionar o evento|Nível|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informativo (4)|

A tabela a seguir mostra as informações do evento:

|Event|ID do evento|Acionado quando|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|A contenção é iniciada. Esse evento não inclui o tempo de rotação antes que um thread aguarde para adquirir um bloqueio; ele é acionado apenas quando o thread aguarda para adquirir um bloqueio.|
|`ContentionStop`|91|A contenção é encerrada.|

A tabela a seguir mostra os dados do evento:

|Nome do campo|Tipo de dados|Descrição|
|----------------|---------------|-----------------|
|Sinalizadores|win:UInt8|0 para gerenciado; 1 para nativo.|
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR.|

## <a name="see-also"></a>Veja também

- [Eventos de CLR ETW](clr-etw-events.md)
