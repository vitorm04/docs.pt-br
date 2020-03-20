---
title: Como criar um serviço que utiliza um validador de certificado personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185570"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="edf72-102">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="edf72-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="edf72-103">Este tópico mostra como implementar um validador de certificado personalizado e como configurar credenciais de cliente ou serviço para substituir a lógica de validação de certificado padrão pelo validador de certificado personalizado.</span><span class="sxs-lookup"><span data-stu-id="edf72-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="edf72-104">Se o certificado X.509 for usado para autenticar um cliente ou serviço, o Windows Communication Foundation (WCF) por padrão usará a loja de certificados Windows e a API Crypto para validar o certificado e garantir que ele seja confiável.</span><span class="sxs-lookup"><span data-stu-id="edf72-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="edf72-105">Às vezes, a funcionalidade de validação de certificado incorporada não é suficiente e deve ser alterada.</span><span class="sxs-lookup"><span data-stu-id="edf72-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="edf72-106">O WCF fornece uma maneira fácil de alterar a lógica de validação, permitindo que os usuários adicionem um validador de certificado personalizado.</span><span class="sxs-lookup"><span data-stu-id="edf72-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="edf72-107">Se um validador de certificado personalizado for especificado, o WCF não usará a lógica de validação de certificado incorporada, mas depende do validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="edf72-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="edf72-108">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="edf72-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="edf72-109">Para criar um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="edf72-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="edf72-110">Defina uma nova <xref:System.IdentityModel.Selectors.X509CertificateValidator>classe derivada de .</span><span class="sxs-lookup"><span data-stu-id="edf72-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="edf72-111">Implementar o <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> método abstrato.</span><span class="sxs-lookup"><span data-stu-id="edf72-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="edf72-112">O certificado que deve ser validado é passado como argumento para o método.</span><span class="sxs-lookup"><span data-stu-id="edf72-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="edf72-113">Se o certificado aprovado não for válido de acordo <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>com a lógica de validação, este método lança um .</span><span class="sxs-lookup"><span data-stu-id="edf72-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="edf72-114">Se o certificado for válido, o método retorna ao chamador.</span><span class="sxs-lookup"><span data-stu-id="edf72-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="edf72-115">Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="edf72-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="edf72-116">Para especificar um validador de certificado personalizado na configuração de serviço</span><span class="sxs-lookup"><span data-stu-id="edf72-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="edf72-117">Adicione [ \<](../../configure-apps/file-schema/wcf/behaviors.md) um elemento>comportamentos e um [ \<>de serviçosComportamento ao](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<elemento system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="edf72-117">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="edf72-118">Adicione [ \<](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` e defina o atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="edf72-118">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="edf72-119">Adicione um [ \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>`>ao elemento.</span><span class="sxs-lookup"><span data-stu-id="edf72-119">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="edf72-120">Adicione `<clientCertificate>` um elemento `<serviceCredentials>` ao elemento.</span><span class="sxs-lookup"><span data-stu-id="edf72-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="edf72-121">Adicione uma [ \<>de autenticação](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ao `<clientCertificate>` elemento.</span><span class="sxs-lookup"><span data-stu-id="edf72-121">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="edf72-122">Defina `customCertificateValidatorType` o atributo para o tipo validador.</span><span class="sxs-lookup"><span data-stu-id="edf72-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="edf72-123">O exemplo a seguir define o atributo para o namespace e nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="edf72-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="edf72-124">Defina `certificateValidationMode` o `Custom`atributo para .</span><span class="sxs-lookup"><span data-stu-id="edf72-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="edf72-125">Para especificar um validador de certificado personalizado usando a configuração no cliente</span><span class="sxs-lookup"><span data-stu-id="edf72-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="edf72-126">Adicione [ \<](../../configure-apps/file-schema/wcf/behaviors.md) um elemento>comportamentos e um [ \<>de serviçosComportamento ao](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<elemento system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="edf72-126">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="edf72-127">Adicione um [ \<elemento>de comportamento de ponto final.](../../configure-apps/file-schema/wcf/endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="edf72-127">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="edf72-128">Adicione um elemento `<behavior>` e defina o atributo `name` para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="edf72-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="edf72-129">Adicione um [ \<elemento de>clientCredentials.](../../configure-apps/file-schema/wcf/clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="edf72-129">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="edf72-130">Adicionar um [ \<serviçoCertificado>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="edf72-130">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="edf72-131">Adicione uma [ \<autenticação>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="edf72-131">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="edf72-132">Defina `customCertificateValidatorType` o atributo para o tipo validador.</span><span class="sxs-lookup"><span data-stu-id="edf72-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="edf72-133">Defina `certificateValidationMode` o `Custom`atributo para .</span><span class="sxs-lookup"><span data-stu-id="edf72-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="edf72-134">O exemplo a seguir define o atributo para o namespace e nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="edf72-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="edf72-135">Para especificar um validador de certificado personalizado usando código no serviço</span><span class="sxs-lookup"><span data-stu-id="edf72-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="edf72-136">Especifique o validador de certificado personalizado na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="edf72-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="edf72-137">Você pode acessar as <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> credenciais de serviço usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="edf72-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="edf72-138">Defina a propriedade <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="edf72-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="edf72-139">Para especificar um validador de certificado personalizado usando código no cliente</span><span class="sxs-lookup"><span data-stu-id="edf72-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="edf72-140">Especifique o validador de certificado personalizado usando a <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="edf72-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="edf72-141">Você pode acessar as <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> credenciais do cliente usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="edf72-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="edf72-142">(A classe cliente gerada pelo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) sempre deriva da <xref:System.ServiceModel.ClientBase%601> classe.)</span><span class="sxs-lookup"><span data-stu-id="edf72-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="edf72-143">Defina a propriedade <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="edf72-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf72-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="edf72-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="edf72-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="edf72-145">Description</span></span>  
 <span data-ttu-id="edf72-146">A amostra a seguir mostra a implementação de um validador de certificado personalizado e seu uso no serviço.</span><span class="sxs-lookup"><span data-stu-id="edf72-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="edf72-147">Código</span><span class="sxs-lookup"><span data-stu-id="edf72-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="edf72-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="edf72-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
