---
title: Evento ETW de pilha
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 073622c22b957975ed799cf5b3bc3826473114b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396348"
---
# <a name="stack-etw-event"></a>Evento ETW de pilha
O evento de pilha deve ser usado em conjunto com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado. Ele é registrado quando o provedor de tempo de execução está habilitado. Esse é um evento de alta frequência porque é acionado sempre que outro evento de tempo de execução é acionado. Por esse motivo, recomendamos ter cautela ao usar esse evento.  
  
 A tabela a seguir mostra a palavra-chave e o nível. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Em conjunto com outros eventos para gerar rastreamentos de pilha após um evento.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:Uint16|Identificador exclusivo do tempo de execução.|  
|Reserved1|win:UInt8|Reservado.|  
|Reserved2|win:UInt8|Reservado.|  
|FrameCount|win:UInt32|O número de quadros no rastreamento de pilha.|  
|Pilha|win:Pointer|Colunas de ponteiros de instrução.|  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
