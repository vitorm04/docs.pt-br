---
title: "Como usar um validador personalizado de nome de usuário e senha"
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
helpviewer_keywords: WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9086489d7b48b459ad92f1712809406cbde7e074
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="6c92e-102">Como usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="6c92e-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="6c92e-103">Por padrão, quando um nome de usuário e uma senha são usados para autenticação, o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usa o Windows para validar esses dados.</span><span class="sxs-lookup"><span data-stu-id="6c92e-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="6c92e-104">No entanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite para esquemas de autenticação de nome e a senha da personalizadas do usuário, também conhecido como *validadores*.</span><span class="sxs-lookup"><span data-stu-id="6c92e-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="6c92e-105">Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.</span><span class="sxs-lookup"><span data-stu-id="6c92e-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="6c92e-106">Para um aplicativo de exemplo, consulte [validador de senha do nome de usuário](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="6c92e-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="6c92e-107">Para criar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="6c92e-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="6c92e-108">Crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="6c92e-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="6c92e-109">Implemente o esquema de autenticação personalizado substituindo o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c92e-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="6c92e-110">Não use o código no exemplo a seguir que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="6c92e-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="6c92e-111">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6c92e-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="6c92e-112">Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c92e-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="6c92e-113">Para configurar um serviço para usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="6c92e-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="6c92e-114">Configure uma associação que usa segurança de mensagem sobre qualquer transporte ou segurança em nível de transporte sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="6c92e-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="6c92e-115">Ao usar a segurança de mensagem, adicione uma das associações fornecidas pelo sistema, como um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que dá suporte à segurança de mensagens e o `UserName` tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="6c92e-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="6c92e-116">Ao usar a segurança em nível de transporte sobre HTTP (S), adicione o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), um [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que usa HTTP (S) e o `Basic` esquema de autenticação.</span><span class="sxs-lookup"><span data-stu-id="6c92e-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c92e-117">Quando [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior é usado, você pode usar um validador personalizado de nome de usuário e senha com a segurança de mensagem e transporte.</span><span class="sxs-lookup"><span data-stu-id="6c92e-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="6c92e-118">Com o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], um validador personalizado de nome de usuário e senha só pode ser usado com segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c92e-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6c92e-119">Para obter mais informações sobre como usar \<netTcpBinding > nesse contexto, consulte [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6c92e-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="6c92e-120">No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6c92e-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="6c92e-121">Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento para a seção de associações.</span><span class="sxs-lookup"><span data-stu-id="6c92e-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6c92e-122">Criando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação elemento, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6c92e-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="6c92e-123">Definir o `mode` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="6c92e-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="6c92e-124">Definir o `clientCredentialType` atributo o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6c92e-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="6c92e-125">Ao usar a segurança de mensagem, defina o `clientCredentialType` atributo o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) para `UserName`.</span><span class="sxs-lookup"><span data-stu-id="6c92e-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="6c92e-126">Ao usar a segurança em nível de transporte sobre HTTP (S), defina o `clientCredentialType` atributo o [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) para `Basic`.</span><span class="sxs-lookup"><span data-stu-id="6c92e-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c92e-127">Quando um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está hospedado nos Serviços de Informações da Internet (IIS) usando a segurança em nível de transporte e a propriedade <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> está definida como <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, o esquema de autenticação personalizada usa um subconjunto de autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6c92e-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="6c92e-128">Isso ocorre porque, neste cenário, o IIS efetua a autenticação do Windows antes de o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chamar o autenticador personalizado.</span><span class="sxs-lookup"><span data-stu-id="6c92e-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6c92e-129">Criando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação elemento, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6c92e-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="6c92e-130">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="6c92e-130">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="6c92e-131">Configure um comportamento que especifica que um validador personalizado de nome de usuário e senha é usado para validar os pares de nome de usuário e senha para tokens de segurança de entrada do <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="6c92e-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="6c92e-132">Como um filho para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6c92e-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="6c92e-133">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6c92e-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="6c92e-134">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="6c92e-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="6c92e-135">Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6c92e-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="6c92e-136">Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="6c92e-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="6c92e-137">Defina o `userNamePasswordValidationMode` como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6c92e-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="6c92e-138">Se o valor de `userNamePasswordValidationMode` não estiver definido, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usará a autenticação do Windows em vez do validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="6c92e-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="6c92e-139">Defina `customUserNamePasswordValidatorType` como o tipo que representa o seu validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="6c92e-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="6c92e-140">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="6c92e-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="6c92e-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c92e-141">Example</span></span>  
 <span data-ttu-id="6c92e-142">O exemplo de código a seguir demonstra como criar um validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="6c92e-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="6c92e-143">Não use o código que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="6c92e-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="6c92e-144">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6c92e-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6c92e-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c92e-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="6c92e-146">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c92e-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="6c92e-147">Autenticação</span><span class="sxs-lookup"><span data-stu-id="6c92e-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
