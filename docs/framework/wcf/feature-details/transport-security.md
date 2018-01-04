---
title: "Segurança de transporte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 364326e2ded11f7174adc891a5fd9bcdd3c98334
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security"></a><span data-ttu-id="f6466-102">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="f6466-102">Transport Security</span></span>
<span data-ttu-id="f6466-103">Segurança de transporte no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] depende da associação selecionada.</span><span class="sxs-lookup"><span data-stu-id="f6466-103">Transport security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] depends on the binding selected.</span></span> <span data-ttu-id="f6466-104">O transporte que implementa a associação determina o mecanismo de segurança real.</span><span class="sxs-lookup"><span data-stu-id="f6466-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="f6466-105">Os tópicos nesta seção explicam os mecanismos que são implementados e suas opções.</span><span class="sxs-lookup"><span data-stu-id="f6466-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6466-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f6466-106">In This Section</span></span>  
 [<span data-ttu-id="f6466-107">Visão geral de segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="f6466-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="f6466-108">Explica os conceitos básicos de segurança de transporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6466-108">Explains the basics of transport security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="f6466-109">Segurança de transporte de HTTP</span><span class="sxs-lookup"><span data-stu-id="f6466-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="f6466-110">Explica como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa Secure Sockets Layer (SSL ou HTTPS).</span><span class="sxs-lookup"><span data-stu-id="f6466-110">Explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="f6466-111">Entendendo a autenticação HTTP</span><span class="sxs-lookup"><span data-stu-id="f6466-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="f6466-112">Descreve os esquemas de autenticação de HTTP, como Basic, Digest, NT LAN Manager (NTLM) e outros.</span><span class="sxs-lookup"><span data-stu-id="f6466-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="f6466-113">Usando a representação com segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="f6466-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="f6466-114">Explica os cinco níveis de representação que são possíveis com o modo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="f6466-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="f6466-115">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="f6466-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="f6466-116">Explica as Noções básicas de configuração de uma porta em um computador com um certificado x. 509 para segurança SSL (transporte).</span><span class="sxs-lookup"><span data-stu-id="f6466-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f6466-117">Referência</span><span class="sxs-lookup"><span data-stu-id="f6466-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="f6466-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f6466-118">Related Sections</span></span>  
 [<span data-ttu-id="f6466-119">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f6466-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6466-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6466-120">See Also</span></span>  
 [<span data-ttu-id="f6466-121">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="f6466-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
