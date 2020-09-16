---
title: Chamadas de Segurança Não Autorizadas por Segundo
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 8aed9f6b8c60c8aecd1b576c13a7063e3a492046
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552499"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="a0269-102">Chamadas de Segurança Não Autorizadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="a0269-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="a0269-103">Nome do contador: chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="a0269-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0269-104">Description</span><span class="sxs-lookup"><span data-stu-id="a0269-104">Description</span></span>  
 <span data-ttu-id="a0269-105">Número de chamadas que falharam na autorização nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="a0269-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="a0269-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método retorna `false` .</span><span class="sxs-lookup"><span data-stu-id="a0269-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="a0269-107">Isso indica que a mensagem de entrada é de um usuário válido e protegida corretamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="a0269-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="a0269-108">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0269-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a0269-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="a0269-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
