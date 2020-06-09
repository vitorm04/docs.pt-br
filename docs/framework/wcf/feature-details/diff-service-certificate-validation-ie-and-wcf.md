---
title: Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 151075f2894b895ab90418748df9face3aa70252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599185"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="f28b0-102">Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF</span><span class="sxs-lookup"><span data-stu-id="f28b0-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="f28b0-103">Devido à diferença entre o modo como o Internet Explorer e o Windows Communication Foundation (WCF) validam certificados de serviço quando o HTTPS é usado, é possível que o Internet Explorer não possa acessar a página de ajuda ou WSDL (Web Services Description Language) de um serviço, mesmo que um cliente WCF seja capaz de enviar mensagens para os pontos de extremidade de serviço com êxito.</span><span class="sxs-lookup"><span data-stu-id="f28b0-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="f28b0-104">Isso ocorre porque o Internet Explorer verifica se o certificado de serviço tem os `ServerAuthentication` identificadores de objeto (OID) nos sinalizadores de uso avançado, enquanto o WCF não impõe essa restrição.</span><span class="sxs-lookup"><span data-stu-id="f28b0-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="f28b0-105">Se o Internet Explorer não puder acessar a página de ajuda do serviço ou o WSDL para o serviço, use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para acessar os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="f28b0-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f28b0-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f28b0-106">See also</span></span>

- [<span data-ttu-id="f28b0-107">Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP</span><span class="sxs-lookup"><span data-stu-id="f28b0-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="f28b0-108">Como recuperar metadados e implementar um serviço em conformidade</span><span class="sxs-lookup"><span data-stu-id="f28b0-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
