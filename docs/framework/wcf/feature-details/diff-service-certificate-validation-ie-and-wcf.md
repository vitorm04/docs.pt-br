---
title: Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225905"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF
Devido a diferença entre a maneira como o Internet Explorer e o Windows Communication Foundation (WCF) validam certificados de serviço quando HTTPS é usado, é possível que a do Internet Explorer não poderá acessar a página de Ajuda ou Web Services Description Language (WSDL) de um serviço mesmo que um cliente WCF com êxito é capaz de enviar mensagens para os pontos de extremidade de serviço. Isso ocorre porque o Internet Explorer verifica se o certificado de serviço tem o `ServerAuthentication` objeto (OID) de identificadores nos sinalizadores de uso avançado, enquanto que o WCF não impõe uma restrição tal. Se o Internet Explorer não consegue acessar a página de ajuda de serviço ou o WSDL para o serviço, use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para acessar os metadados de serviço.  
  
## <a name="see-also"></a>Consulte também

- [Diferenças de validação de certificado entre HTTPS, SSL sobre TCP e segurança SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Como: Recuperar metadados e implementar um serviço em conformidade](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
