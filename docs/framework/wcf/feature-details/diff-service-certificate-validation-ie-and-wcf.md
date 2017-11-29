---
title: "Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a58ea9f84571ede9943769e1f187a242383a88f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="bff10-102">Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF</span><span class="sxs-lookup"><span data-stu-id="bff10-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="bff10-103">Devido a diferença entre a forma como o Internet Explorer e [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validar certificados de serviço quando HTTPS é usado, é possível que a Internet Explorer não poderá acessar a página de Ajuda ou WSDL Web Services Description Language () de um serviço, mesmo Embora um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é capaz de enviar mensagens com êxito para os pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="bff10-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="bff10-104">Isso ocorre porque o Internet Explorer verifica se o certificado de serviço tem o `ServerAuthentication` objeto (OID) de identificadores nos sinalizadores de uso avançado, enquanto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não impõe uma restrição tal.</span><span class="sxs-lookup"><span data-stu-id="bff10-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="bff10-105">Se o Internet Explorer não é possível acessar a página de ajuda de serviço ou o WSDL para o serviço, use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para acessar os metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="bff10-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff10-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bff10-106">See Also</span></span>  
 [<span data-ttu-id="bff10-107">Diferenças de validação de certificado entre HTTPS, SSL através de TCP e segurança SOAP</span><span class="sxs-lookup"><span data-stu-id="bff10-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="bff10-108">Como: recuperar metadados e implementar um serviço compatível</span><span class="sxs-lookup"><span data-stu-id="bff10-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
