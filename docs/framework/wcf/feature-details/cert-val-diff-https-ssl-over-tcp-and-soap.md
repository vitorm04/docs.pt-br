---
title: "Diferenças de validação de certificado entre segurança de SOAP, HTTPS, SSL através de TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Diferenças de validação de certificado entre segurança de SOAP, HTTPS, SSL através de TCP
Você pode usar certificados no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] com segurança de camada de mensagem (SOAP) além da segurança de camada de transporte (TLS) via HTTP (HTTPS) ou TCP. Este tópico descreve as diferenças no modo como esses certificados são validados.  
  
## <a name="validation-of-https-client-certificates"></a>Validação de certificados de cliente HTTPS  
 Ao usar HTTPS para comunicação entre um cliente e um serviço, o certificado que o cliente usa para autenticar o serviço deve dar suporte a relação de confiança de cadeia. Ou seja, ele deve se encadear a uma autoridade de certificação raiz confiável. Se não, a camada HTTP gera um <xref:System.Net.WebException> com a mensagem "o servidor remoto retornou um erro: proibido (403)." [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]revelam essa exceção como um <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Validação de certificados de serviço HTTPS  
 Quando usando HTTPS para comunicação entre um cliente e um serviço, o certificado que o servidor autentica com deve dar suporte a cadeia de confiança por padrão. Ou seja, ele deve se encadear a uma autoridade de certificação raiz confiável. Nenhuma verificação online é executada para ver se o certificado foi revogado. Você pode substituir esse comportamento Registrando um <xref:System.Net.Security.RemoteCertificateValidationCallback> retorno de chamada, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 onde a assinatura para `ValidateServerCertificate` é o seguinte:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementando `ValidateServerCertificate` pode executar verificações de que o desenvolvedor do aplicativo cliente considere necessário para validar o certificado de serviço.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Validação de certificados de cliente no SSL sobre TCP ou segurança SOAP  
 Quando usando o protocolo (SSL) sobre TCP ou segurança de mensagem (SOAP), os certificados de cliente são validados de acordo com o <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores. Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Validação do certificado de serviço no SSL sobre TCP e segurança SOAP  
 Ao usar SSL sobre segurança de mensagem (SOAP) ou TCP, certificados de serviço são validados de acordo com o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores.  
  
 Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
