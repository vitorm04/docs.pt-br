---
title: Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0e82d1898bec7cda474a5a92958b5af1b30c9de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185400"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Diferentes validações de certificado entre segurança de SOAP, HTTPS, SSL através de TCP
Você pode usar certificados no Windows Communication Foundation (WCF) com segurança de camada de mensagem (SOAP), além de TLS (Transport-Layer Security, segurança em camadade transporte) sobre HTTP (HTTPS) ou TCP. Este tópico descreve diferenças na forma como esses certificados são validados.  
  
## <a name="validation-of-https-client-certificates"></a>Validação de Certificados de Cliente SC  
 Ao usar https para se comunicar entre um cliente e um serviço, o certificado que o cliente usa para autenticar ao serviço deve suportar a confiança da cadeia. Ou seja, deve ser acorrentado a uma autoridade de certificado raiz confiável. Caso assim, a camada <xref:System.Net.WebException> HTTP levanta um com a mensagem "O servidor remoto retornou um erro: (403) Proibido". O WCF aparece nesta <xref:System.ServiceModel.Security.MessageSecurityException>exceção como um .  
  
## <a name="validation-of-https-service-certificates"></a>Validação de Certificados de Serviço HTTPS  
 Ao usar https para se comunicar entre um cliente e um serviço, o certificado com o que o servidor autentica deve suportar a confiança da cadeia por padrão. Ou seja, deve ser acorrentado a uma autoridade de certificado raiz confiável. Nenhuma verificação on-line é realizada para ver se o certificado foi revogado. Você pode anular esse comportamento <xref:System.Net.Security.RemoteCertificateValidationCallback> registrando um retorno de chamada, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 onde a `ValidateServerCertificate` assinatura é a seguinte:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 A `ValidateServerCertificate` implementação pode realizar quaisquer verificações que o desenvolvedor de aplicativos cliente considere necessário para validar o certificado de serviço.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Validação de certificados de cliente em SSL sobre segurança TCP ou SOAP  
 Ao usar a Camada de Soquetes Seguros (SSL) sobre a segurança <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> TCP <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> ou mensagem (SOAP), os certificados de cliente são validados de acordo com o valor de propriedade da classe. A propriedade é definida <xref:System.ServiceModel.Security.X509CertificateValidationMode> como um dos valores. A verificação da revogação é <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> realizada de <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> acordo com os valores do valor patrimonial da classe. A propriedade é definida <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> como um dos valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Validação do Certificado de Serviço em SSL sobre segurança TCP e SOAP  
 Ao usar ssl sobre segurança de mensagens TCP ou (SOAP), os certificados de serviço são validados de acordo com o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> valor de propriedade da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe. A propriedade é definida <xref:System.ServiceModel.Security.X509CertificateValidationMode> como um dos valores.  
  
 A verificação da revogação é <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> realizada de <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> acordo com os valores do valor patrimonial da classe. A propriedade é definida <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> como um dos valores.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
