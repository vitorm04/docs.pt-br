---
title: 'Serviço: chamadas de segurança não autorizadas'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: eb0f0d3e3005a4efca27ec3a63e2a854f735258b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="d591b-102">Serviço: chamadas de segurança não autorizadas</span><span class="sxs-lookup"><span data-stu-id="d591b-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="d591b-103">Nome do contador: Chamadas de segurança não autorizadas.</span><span class="sxs-lookup"><span data-stu-id="d591b-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d591b-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d591b-104">Description</span></span>  
 <span data-ttu-id="d591b-105">Esse contador é incrementado quando o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="d591b-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d591b-106">Ele indica que a mensagem de entrada é de um usuário válido e protegido adequadamente, mas o usuário não está autorizado a realizar tarefas específicas.</span><span class="sxs-lookup"><span data-stu-id="d591b-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
