---
title: "Chamadas de segurança não autorizadas por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 73500901b89eb2cb61fe34895ce6ba150b7e3357
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="d8386-102">Chamadas de segurança não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="d8386-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="d8386-103">Nome do contador: Chamadas de segurança não autorizadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="d8386-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8386-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8386-104">Description</span></span>  
 <span data-ttu-id="d8386-105">Número de chamadas que apresentaram falha de autorização nesta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="d8386-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="d8386-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="d8386-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d8386-107">Ele indica que a mensagem de entrada é de um usuário válido e protegido adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="d8386-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="d8386-108">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="d8386-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8386-109">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d8386-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
