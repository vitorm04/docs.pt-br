---
title: 'Ponto de extremidade: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
ms.openlocfilehash: 4abea795eb196d339beec17fa7a171927aa85324
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078364"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="6e838-102">Ponto de extremidade: chamadas de segurança não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="6e838-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="6e838-103">Nome do contador: Chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="6e838-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6e838-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e838-104">Description</span></span>  
 <span data-ttu-id="6e838-105">Número de mensagens de entrada em um segundo de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="6e838-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="6e838-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`.</span><span class="sxs-lookup"><span data-stu-id="6e838-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="6e838-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e838-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6e838-108">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6e838-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
