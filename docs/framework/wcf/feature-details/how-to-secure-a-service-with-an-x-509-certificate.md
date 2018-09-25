---
title: Como proteger um serviço com um certificado X.509
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
author: BrucePerlerMS
ms.openlocfilehash: 1c5ab5e76ebed549df09b365a5a271f81003a517
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073548"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Como proteger um serviço com um certificado X.509
Proteger um serviço com um certificado X.509 é uma técnica básica que usam a maioria das ligações no Windows Communication Foundation (WCF). Este tópico explica as etapas de configuração de um serviço auto-hospedado com um certificado X.509.  
  
 Um pré-requisito é um certificado válido que pode ser usado para autenticar o servidor. O certificado deve ser emitido para o servidor por uma autoridade de certificação confiável. Se o certificado não é válido, qualquer tentativa de usar o serviço de cliente não confiará o serviço e, consequentemente, nenhuma conexão será feita. Para obter mais informações sobre como usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Para configurar um serviço com um certificado usando código  
  
1.  Crie o contrato de serviço e o serviço implementado. Para obter mais informações, consulte [projetar e implementar serviços](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2.  Criar uma instância das <xref:System.ServiceModel.WSHttpBinding> de classe e definir seu modo de segurança <xref:System.ServiceModel.SecurityMode.Message>, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  Crie duas <xref:System.Type> variáveis, um para o tipo de contrato e o contrato implementado, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  Criar uma instância da <xref:System.Uri> classe para o endereço base do serviço. Porque o `WSHttpBinding` usa o transporte HTTP, o identificador de recurso uniforme (URI) deve começar com esse esquema, ou o Windows Communication Foundation (WCF) lançará uma exceção quando o serviço é aberto.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  Criar uma nova instância do <xref:System.ServiceModel.ServiceHost> classe com a variável de tipo de contrato implementada e o URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> ao serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método. Passe o contrato, associação e um endereço de ponto de extremidade para o construtor, conforme mostrado no código a seguir.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  Opcional. Para recuperar metadados do serviço, crie um novo <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do objeto e defina o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para adicionar o certificado válido para o serviço. O método pode usar um dos vários métodos para localizar um certificado. Este exemplo usa o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeração. A enumeração Especifica que o valor fornecido é o nome da entidade que o certificado foi emitido para.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Chamar o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método para iniciar o serviço escuta. Se você estiver criando um aplicativo de console, chame o <xref:System.Console.ReadLine%2A> método para manter o serviço no estado de escuta.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método para configurar um serviço com um certificado X.509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os seguintes namespaces são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
