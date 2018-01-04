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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12e30d9df9d6bb0a9f8776099951e4354d302ebf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Diferenças entre validação de certificado de serviço pelo Internet Explorer e o WCF
Devido a diferença entre a forma como o Internet Explorer e [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validar certificados de serviço quando HTTPS é usado, é possível que a Internet Explorer não poderá acessar a página de Ajuda ou WSDL Web Services Description Language () de um serviço, mesmo Embora um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente é capaz de enviar mensagens com êxito para os pontos de extremidade de serviço. Isso ocorre porque o Internet Explorer verifica se o certificado de serviço tem o `ServerAuthentication` objeto (OID) de identificadores nos sinalizadores de uso avançado, enquanto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não impõe uma restrição tal. Se o Internet Explorer não é possível acessar a página de ajuda de serviço ou o WSDL para o serviço, use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para acessar os metadados de serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Diferenças de validação de certificado entre HTTPS, SSL sobre TCP e segurança SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Como recuperar metadados e implementar um serviço em conformidade](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
