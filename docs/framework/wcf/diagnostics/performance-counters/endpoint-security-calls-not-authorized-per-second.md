---
title: 'Ponto de extremidade: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163170"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="fee44-102">Ponto de extremidade: chamadas de segurança não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="fee44-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="fee44-103">Nome do contador: chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="fee44-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fee44-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fee44-104">Description</span></span>  
 <span data-ttu-id="fee44-105">Número de mensagens de entrada em um segundo que são de um usuário válido e protegidas corretamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="fee44-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="fee44-106">Esse contador é incrementado quando o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="fee44-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="fee44-107">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="fee44-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fee44-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="fee44-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
