---
title: Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0ab343da821e8994ac3a652bfc55db261d5e48f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857643"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP
Você pode usar certificados no Windows Communication Foundation (WCF) com a segurança de camada de mensagem (SOAP) além da segurança de camada de transporte (TLS) sobre HTTPS (HTTP) ou TCP. Este tópico descreve as diferenças na maneira como esses certificados são validados.  
  
## <a name="validation-of-https-client-certificates"></a>Validação de certificados de cliente HTTPS  
 Ao usar HTTPS para comunicação entre um cliente e um serviço, o certificado que o cliente usa para autenticar o serviço deve dar suporte a relação de confiança de cadeia. Ou seja, ele deve encadear para uma autoridade de certificação raiz confiável. Se não, a camada HTTP aciona uma <xref:System.Net.WebException> com a mensagem "o servidor remoto retornou um erro: (403) proibido." O WCF expõe essa exceção como um <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Validação de certificados de serviço do HTTPS  
 Ao usar HTTPS para comunicação entre um cliente e um serviço, o certificado que o servidor autentica com deve oferecer suporte confiança de cadeia por padrão. Ou seja, ele deve encadear para uma autoridade de certificação raiz confiável. Nenhuma verificação online é executada para ver se o certificado foi revogado. Você pode substituir esse comportamento, registrando um <xref:System.Net.Security.RemoteCertificateValidationCallback> retorno de chamada, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 em que a assinatura para `ValidateServerCertificate` é da seguinte maneira:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementando `ValidateServerCertificate` pode executar nenhuma verificação de que o desenvolvedor do aplicativo cliente considera necessário para validar o certificado de serviço.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Validação de certificados de cliente no SSL sobre TCP ou segurança SOAP  
 Quando usando Secure Sockets Layer (SSL) sobre TCP ou segurança de mensagem (SOAP), certificados de cliente são validados de acordo com o <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade a <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores. Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> valor da propriedade a <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Validação do certificado de serviço no SSL sobre TCP e segurança SOAP  
 Ao usar SSL sobre segurança de mensagem TCP ou (SOAP), certificados de serviço são validados de acordo com o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade a <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores.  
  
 Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> valor da propriedade a <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe. A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
