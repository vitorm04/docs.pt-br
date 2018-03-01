---
title: "Diferenças de validação de certificado entre segurança de SOAP, HTTPS, SSL através de TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="ef1da-102">Diferenças de validação de certificado entre segurança de SOAP, HTTPS, SSL através de TCP</span><span class="sxs-lookup"><span data-stu-id="ef1da-102">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>
<span data-ttu-id="ef1da-103">Você pode usar certificados no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] com segurança de camada de mensagem (SOAP) além da segurança de camada de transporte (TLS) via HTTP (HTTPS) ou TCP.</span><span class="sxs-lookup"><span data-stu-id="ef1da-103">You can use certificates in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="ef1da-104">Este tópico descreve as diferenças no modo como esses certificados são validados.</span><span class="sxs-lookup"><span data-stu-id="ef1da-104">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="ef1da-105">Validação de certificados de cliente HTTPS</span><span class="sxs-lookup"><span data-stu-id="ef1da-105">Validation of HTTPS Client Certificates</span></span>  
 <span data-ttu-id="ef1da-106">Ao usar HTTPS para comunicação entre um cliente e um serviço, o certificado que o cliente usa para autenticar o serviço deve dar suporte a relação de confiança de cadeia.</span><span class="sxs-lookup"><span data-stu-id="ef1da-106">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="ef1da-107">Ou seja, ele deve se encadear a uma autoridade de certificação raiz confiável.</span><span class="sxs-lookup"><span data-stu-id="ef1da-107">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="ef1da-108">Se não, a camada HTTP gera um <xref:System.Net.WebException> com a mensagem "o servidor remoto retornou um erro: proibido (403)."</span><span class="sxs-lookup"><span data-stu-id="ef1da-108">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ef1da-109">revelam essa exceção como um <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="ef1da-109"> surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="ef1da-110">Validação de certificados de serviço HTTPS</span><span class="sxs-lookup"><span data-stu-id="ef1da-110">Validation of HTTPS Service Certificates</span></span>  
 <span data-ttu-id="ef1da-111">Quando usando HTTPS para comunicação entre um cliente e um serviço, o certificado que o servidor autentica com deve dar suporte a cadeia de confiança por padrão.</span><span class="sxs-lookup"><span data-stu-id="ef1da-111">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="ef1da-112">Ou seja, ele deve se encadear a uma autoridade de certificação raiz confiável.</span><span class="sxs-lookup"><span data-stu-id="ef1da-112">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="ef1da-113">Nenhuma verificação online é executada para ver se o certificado foi revogado.</span><span class="sxs-lookup"><span data-stu-id="ef1da-113">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="ef1da-114">Você pode substituir esse comportamento Registrando um <xref:System.Net.Security.RemoteCertificateValidationCallback> retorno de chamada, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef1da-114">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="ef1da-115">onde a assinatura para `ValidateServerCertificate` é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ef1da-115">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="ef1da-116">Implementando `ValidateServerCertificate` pode executar verificações de que o desenvolvedor do aplicativo cliente considere necessário para validar o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef1da-116">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="ef1da-117">Validação de certificados de cliente no SSL sobre TCP ou segurança SOAP</span><span class="sxs-lookup"><span data-stu-id="ef1da-117">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  
 <span data-ttu-id="ef1da-118">Quando usando o protocolo (SSL) sobre TCP ou segurança de mensagem (SOAP), os certificados de cliente são validados de acordo com o <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="ef1da-118">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="ef1da-119">A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores.</span><span class="sxs-lookup"><span data-stu-id="ef1da-119">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="ef1da-120">Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="ef1da-120">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="ef1da-121">A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.</span><span class="sxs-lookup"><span data-stu-id="ef1da-121">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="ef1da-122">Validação do certificado de serviço no SSL sobre TCP e segurança SOAP</span><span class="sxs-lookup"><span data-stu-id="ef1da-122">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  
 <span data-ttu-id="ef1da-123">Ao usar SSL sobre segurança de mensagem (SOAP) ou TCP, certificados de serviço são validados de acordo com o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="ef1da-123">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="ef1da-124">A propriedade é definida como um do <xref:System.ServiceModel.Security.X509CertificateValidationMode> valores.</span><span class="sxs-lookup"><span data-stu-id="ef1da-124">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="ef1da-125">Verificação de revogação é executada de acordo com os valores da <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> valor da propriedade de <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="ef1da-125">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="ef1da-126">A propriedade é definida como um do <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valores.</span><span class="sxs-lookup"><span data-stu-id="ef1da-126">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ef1da-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef1da-127">See Also</span></span>  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [<span data-ttu-id="ef1da-128">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="ef1da-128">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
