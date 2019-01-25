---
title: 'Como: Obter um certificado (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: cefea47d77fef9a59234584b02b03dca4cd99ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709436"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="d6d49-102">Como: Obter um certificado (WCF)</span><span class="sxs-lookup"><span data-stu-id="d6d49-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="d6d49-103">Use qualquer um do Windows Communication Foundation (WCF) recursos do que usam certificados X.509, você apenas primeiro obter certificados.</span><span class="sxs-lookup"><span data-stu-id="d6d49-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="d6d49-104">Para obter um certificado x. 509</span><span class="sxs-lookup"><span data-stu-id="d6d49-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="d6d49-105">Escolha uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d6d49-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="d6d49-106">Compre um certificado de uma autoridade de certificação, como VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="d6d49-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="d6d49-107">Configurar seu próprio serviço de certificado e ter uma autoridade de certificação assinar os certificados.</span><span class="sxs-lookup"><span data-stu-id="d6d49-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="d6d49-108">, Windows 2000 Server, o Windows 2000 Server Datacenter e o Windows 2000 Datacenter Server incluem serviços de certificados que dão suporte à infraestrutura de chave pública (PKI).</span><span class="sxs-lookup"><span data-stu-id="d6d49-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="d6d49-109">No Windows Server 2008, use o [serviços de certificados do Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) função para gerenciar uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="d6d49-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="d6d49-110">Configurar seu próprio serviço de certificado e não têm os certificados assinados.</span><span class="sxs-lookup"><span data-stu-id="d6d49-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d6d49-111">Qualquer abordagem, o destinatário da solicitação SOAP que contém o certificado X.509 deve confiar no certificado de x. 509.</span><span class="sxs-lookup"><span data-stu-id="d6d49-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="d6d49-112">Isso significa que o certificado X.509 ou um emissor na cadeia de certificados no repositório de certificados pessoas confiáveis e que não é o certificado X.509 no repositório de certificados não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d6d49-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d49-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6d49-113">See also</span></span>
- [<span data-ttu-id="d6d49-114">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="d6d49-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d6d49-115">Como: Criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="d6d49-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
