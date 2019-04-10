---
title: 'Como: proteger um serviço com um certificado X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 75c7a0e50301ce80d51b9b2a10ed650a1600ec79
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300080"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="d14f4-102">Como: proteger um serviço com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="d14f4-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="d14f4-103">Proteger um serviço com um certificado X.509 é uma técnica básica que usam a maioria das ligações no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d14f4-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="d14f4-104">Este tópico explica as etapas de configuração de um serviço auto-hospedado com um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d14f4-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="d14f4-105">Um pré-requisito é um certificado válido que pode ser usado para autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="d14f4-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="d14f4-106">O certificado deve ser emitido para o servidor por uma autoridade de certificação confiável.</span><span class="sxs-lookup"><span data-stu-id="d14f4-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="d14f4-107">Se o certificado não é válido, qualquer tentativa de usar o serviço de cliente não confiará o serviço e, consequentemente, nenhuma conexão será feita.</span><span class="sxs-lookup"><span data-stu-id="d14f4-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="d14f4-108">Para obter mais informações sobre como usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d14f4-108">For more information about using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="d14f4-109">Para configurar um serviço com um certificado usando código</span><span class="sxs-lookup"><span data-stu-id="d14f4-109">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="d14f4-110">Crie o contrato de serviço e o serviço implementado.</span><span class="sxs-lookup"><span data-stu-id="d14f4-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="d14f4-111">Para obter mais informações, consulte [projetar e implementar serviços](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="d14f4-111">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="d14f4-112">Criar uma instância das <xref:System.ServiceModel.WSHttpBinding> de classe e definir seu modo de segurança <xref:System.ServiceModel.SecurityMode.Message>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="d14f4-113">Crie duas <xref:System.Type> variáveis, um para o tipo de contrato e o contrato implementado, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="d14f4-114">Criar uma instância da <xref:System.Uri> classe para o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="d14f4-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="d14f4-115">Porque o `WSHttpBinding` usa o transporte HTTP, o identificador de recurso uniforme (URI) deve começar com esse esquema, ou o Windows Communication Foundation (WCF) lançará uma exceção quando o serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="d14f4-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="d14f4-116">Criar uma nova instância do <xref:System.ServiceModel.ServiceHost> classe com a variável de tipo de contrato implementada e o URI.</span><span class="sxs-lookup"><span data-stu-id="d14f4-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="d14f4-117">Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> ao serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d14f4-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="d14f4-118">Passe o contrato, associação e um endereço de ponto de extremidade para o construtor, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="d14f4-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d14f4-119">Optional.</span></span> <span data-ttu-id="d14f4-120">Para recuperar metadados do serviço, crie um novo <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do objeto e defina o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="d14f4-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="d14f4-121">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para adicionar o certificado válido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="d14f4-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="d14f4-122">O método pode usar um dos vários métodos para localizar um certificado.</span><span class="sxs-lookup"><span data-stu-id="d14f4-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="d14f4-123">Este exemplo usa o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeração.</span><span class="sxs-lookup"><span data-stu-id="d14f4-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="d14f4-124">A enumeração Especifica que o valor fornecido é o nome da entidade que o certificado foi emitido para.</span><span class="sxs-lookup"><span data-stu-id="d14f4-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="d14f4-125">Chamar o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método para iniciar o serviço escuta.</span><span class="sxs-lookup"><span data-stu-id="d14f4-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="d14f4-126">Se você estiver criando um aplicativo de console, chame o <xref:System.Console.ReadLine%2A> método para manter o serviço no estado de escuta.</span><span class="sxs-lookup"><span data-stu-id="d14f4-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="d14f4-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d14f4-127">Example</span></span>  
 <span data-ttu-id="d14f4-128">O exemplo a seguir usa o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método para configurar um serviço com um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="d14f4-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d14f4-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d14f4-129">Compiling the Code</span></span>  
 <span data-ttu-id="d14f4-130">Os seguintes namespaces são necessários para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="d14f4-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="d14f4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d14f4-131">See also</span></span>

- [<span data-ttu-id="d14f4-132">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="d14f4-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
