---
title: Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225905"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="b0bb0-102">Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF</span><span class="sxs-lookup"><span data-stu-id="b0bb0-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="b0bb0-103">Devido a diferença entre a maneira como o Internet Explorer e o Windows Communication Foundation (WCF) validam certificados de serviço quando HTTPS é usado, é possível que a do Internet Explorer não poderá acessar a página de Ajuda ou Web Services Description Language (WSDL) de um serviço mesmo que um cliente WCF com êxito é capaz de enviar mensagens para os pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0bb0-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="b0bb0-104">Isso ocorre porque o Internet Explorer verifica se o certificado de serviço tem o `ServerAuthentication` objeto (OID) de identificadores nos sinalizadores de uso avançado, enquanto que o WCF não impõe uma restrição tal.</span><span class="sxs-lookup"><span data-stu-id="b0bb0-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="b0bb0-105">Se o Internet Explorer não consegue acessar a página de ajuda de serviço ou o WSDL para o serviço, use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para acessar os metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0bb0-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0bb0-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0bb0-106">See also</span></span>

- [<span data-ttu-id="b0bb0-107">Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP</span><span class="sxs-lookup"><span data-stu-id="b0bb0-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="b0bb0-108">Como: recuperar metadados e implementar um serviço em conformidade</span><span class="sxs-lookup"><span data-stu-id="b0bb0-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
