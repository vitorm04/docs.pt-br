---
title: 'Serviço: chamadas de segurança não autorizadas por segundo'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399407"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="e97dd-102">Serviço: chamadas de segurança não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="e97dd-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="e97dd-103">Nome do contador: segurança chamadas não autorizadas por segundo</span><span class="sxs-lookup"><span data-stu-id="e97dd-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e97dd-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e97dd-104">Description</span></span>  
 <span data-ttu-id="e97dd-105">Número de mensagens de entrada em um segundo, que são de um usuário válido e protegidas adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="e97dd-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="e97dd-106">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retorno do método `false`.</span><span class="sxs-lookup"><span data-stu-id="e97dd-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="e97dd-107">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="e97dd-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e97dd-108">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e97dd-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
