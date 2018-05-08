---
title: Como fazer referência de forma consistente aos certificados X.509
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: efc4fb399224de7f03c6bffb606178184de1d467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Como fazer referência de forma consistente aos certificados X.509
Você pode identificar um certificado de várias maneiras: pelo hash do certificado, o emissor e número de série ou pelo identificador de chave de assunto (SKI). O SKI fornece uma identificação exclusiva para a chave pública da entidade do certificado e geralmente é usada ao trabalhar com a assinatura digital XML. O valor SKI geralmente é parte do certificado x. 509 como um *a extensão de certificado x. 509*. Windows Communication Foundation (WCF) tem um padrão *referenciando estilo* que usa o emissor e número de série, se a extensão SKI está ausente no certificado. Se o certificado contém a extensão SKI, o padrão de referência de estilo usa o SKI para apontar para o certificado. Se a forma intermediário durante o desenvolvimento de um aplicativo, você alternar do uso de certificados que não usam a extensão SKI para certificados que usam a extensão SKI, também altera o estilo de referência usado em mensagens geradas pelo WCF.  
  
 Se um estilo consistente de referência for exigido, independentemente da presença da extensão SKI, é possível configurar o estilo de referência desejado, como mostrado no código a seguir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento de associação de segurança personalizada que usa um único estilo de referência consistente, o nome do emissor e número de série.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os namespaces a seguir são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
