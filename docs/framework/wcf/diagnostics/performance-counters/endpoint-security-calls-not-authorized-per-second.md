---
title: "Ponto de extremidade: chamadas de segurança não autorizadas por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 50bb92a31af3775f17868c7057a160f64a82f0b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="94906-102">Ponto de extremidade: chamadas de segurança não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="94906-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="94906-103">Nome do contador: Chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="94906-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="94906-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="94906-104">Description</span></span>  
 <span data-ttu-id="94906-105">Número de mensagens de entrada em um segundo de um usuário válido e protegido adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="94906-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="94906-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="94906-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="94906-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="94906-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="94906-108">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="94906-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
