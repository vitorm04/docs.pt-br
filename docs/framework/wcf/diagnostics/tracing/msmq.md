---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663720"
---
# <a name="msmq"></a>MSMQ
Em um aplicativo do MSMQ, nenhuma atividade adicional é transferida do canal na fila para o MSMQ e MSMQ para o canal em fila.  
  
 Além disso, a ID de mensagem do MSMQ e a ID da mensagem SOAP (juntamente com a ID da atividade, se houver) são rastreados como parte dos rastreamentos de canal em fila em uma operação de envio.  
  
 ID de mensagem do MSMQ e a ID da mensagem SOAP (juntamente com a atividade de ID, se um existe) são rastreados como parte dos rastreamentos de canal em fila em uma operação de recebimento.  
  
 As transferências necessárias na operação de recebimento são executadas da mesma forma para qualquer outro transporte (receber bytes de mensagem do processo -> -> operação).
