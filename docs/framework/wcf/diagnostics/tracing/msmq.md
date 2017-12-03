---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a><span data-ttu-id="df119-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="df119-102">MSMQ</span></span>
<span data-ttu-id="df119-103">Em um aplicativo do MSMQ, nenhuma atividade adicional é transferida do canal em fila MSMQ e MSMQ no canal em fila.</span><span class="sxs-lookup"><span data-stu-id="df119-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="df119-104">Além disso, a ID de mensagem do MSMQ e a ID de mensagem SOAP (junto com a ID da atividade, se houver) são rastreadas como parte de rastreamentos de canal em fila em uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="df119-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="df119-105">ID de mensagem do MSMQ e a ID de mensagem SOAP (juntamente com a atividade de ID, se existe) são rastreadas como parte de rastreamentos de canal em fila em uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="df119-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="df119-106">As transferências necessárias na operação de recebimento são executadas da mesma forma para qualquer outro transporte (receber bytes de mensagem de processo -> -> operação).</span><span class="sxs-lookup"><span data-stu-id="df119-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
