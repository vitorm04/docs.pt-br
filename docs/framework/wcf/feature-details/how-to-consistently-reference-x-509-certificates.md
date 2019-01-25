---
title: 'Como: Consistentemente certificados X.509 de referência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2468faabfbca57e7d905a592b6743c43cb2ccd56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731966"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Como: Consistentemente certificados X.509 de referência
Você pode identificar um certificado de várias maneiras: pelo hash do certificado, o emissor e número de série ou pelo identificador de chave de assunto (SKI). O SKI fornece uma identificação exclusiva para chave pública do assunto do certificado e geralmente é usado ao trabalhar com a assinatura digital XML. O valor de ESQUI geralmente é parte do certificado X.509 como uma *extensão de certificado x. 509*. Windows Communication Foundation (WCF) tem um padrão *referenciando estilo* se a extensão de ESQUI está ausente no certificado que usa o emissor e número de série. Se o certificado contém a extensão de ESQUI, o padrão de estilo de referência usa o SKI para apontar para o certificado. Se a forma intermediário por meio do desenvolvimento de um aplicativo, você alterna o uso de certificados que não usam a extensão de ESQUI a certificados que usam a extensão de ESQUI, também altera o estilo de referência usado em mensagens geradas pelo WCF.  
  
 Se um estilo consistente de referência for necessário, independentemente da presença da extensão de ESQUI, é possível configurar o estilo de referência desejado, conforme mostrado no código a seguir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento de associação de segurança personalizada que usa um único estilo de referência consistente, o nome do emissor e número de série.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os seguintes namespaces são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Consulte também
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
