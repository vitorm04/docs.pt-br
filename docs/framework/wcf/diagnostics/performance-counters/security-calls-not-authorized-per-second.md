---
title: Chamadas de Segurança Não Autorizadas por Segundo
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
ms.openlocfilehash: 20c8da5fcdca0c99fd53fb5ce0d7cbf15552997a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192256"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="d9489-102">Chamadas de Segurança Não Autorizadas por Segundo</span><span class="sxs-lookup"><span data-stu-id="d9489-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="d9489-103">Nome do contador: Chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="d9489-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9489-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9489-104">Description</span></span>  
 <span data-ttu-id="d9489-105">Número de chamadas com falha de autorização nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="d9489-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="d9489-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`.</span><span class="sxs-lookup"><span data-stu-id="d9489-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d9489-107">Ele indica que a mensagem de entrada é de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="d9489-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="d9489-108">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="d9489-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d9489-109">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d9489-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
