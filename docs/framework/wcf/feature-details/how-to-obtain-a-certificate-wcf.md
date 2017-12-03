---
title: Como obter um certificado (WCF)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1b7ab4ed91487965ac8b0d78a9a44818cfee9eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="aa6d9-102">Como obter um certificado (WCF)</span><span class="sxs-lookup"><span data-stu-id="aa6d9-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="aa6d9-103">Usar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recursos que usam certificados x. 509, apenas o primeiro obter certificados.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="aa6d9-104">Para obter um certificado x. 509</span><span class="sxs-lookup"><span data-stu-id="aa6d9-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="aa6d9-105">Escolha uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="aa6d9-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="aa6d9-106">Compre um certificado de uma autoridade de certificação, como VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="aa6d9-107">Configurar seu próprio serviço de certificado e ter uma autoridade de certificação assinar os certificados.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="aa6d9-108">, Windows 2000 Server, o Windows 2000 Server Datacenter e o Windows 2000 Datacenter Server incluem os serviços de certificados que oferecem suporte à infraestrutura de chave pública (PKI).</span><span class="sxs-lookup"><span data-stu-id="aa6d9-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="aa6d9-109">No Windows Server 2008, use o [serviços de certificados do Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) função para gerenciar uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="aa6d9-110">Configurar seu próprio serviço de certificado e fazer não tem certificados assinados.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa6d9-111">Qualquer abordagem, o destinatário da solicitação SOAP que contém o certificado x. 509 deve confiar no certificado de x. 509.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="aa6d9-112">Isso significa que o certificado x. 509 ou um emissor da cadeia de certificados no repositório de certificados de pessoas confiáveis e que o certificado x. 509 não está no repositório de certificados não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="aa6d9-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6d9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa6d9-113">See Also</span></span>  
 [<span data-ttu-id="aa6d9-114">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="aa6d9-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="aa6d9-115">Como: criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="aa6d9-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
