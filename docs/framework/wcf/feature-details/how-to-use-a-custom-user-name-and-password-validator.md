---
title: 'Como: usar um validador personalizado de nome de usuário e senha'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 57bd650caef831f3ee886c0422e13cc4149d3416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968803"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d0f6b-102">Como: usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="d0f6b-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="d0f6b-103">Por padrão, quando um nome de usuário e uma senha são usados para autenticação, Windows Communication Foundation (WCF) usa o Windows para validar o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="d0f6b-104">No entanto, o WCF permite esquemas de autenticação de senha e nome de usuáriopersonalizados, também conhecidos como validadores.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="d0f6b-105">Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="d0f6b-106">Para obter um aplicativo de exemplo, consulte o validador de [senha do nome de usuário](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6b-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d0f6b-107">Para criar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="d0f6b-107">To create a custom user name and password validator</span></span>  
  
1. <span data-ttu-id="d0f6b-108">Crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. <span data-ttu-id="d0f6b-109">Implemente o esquema de autenticação personalizado substituindo o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="d0f6b-110">Não use o código no exemplo a seguir que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d0f6b-111">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="d0f6b-112">Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d0f6b-113">Para configurar um serviço para usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="d0f6b-113">To configure a service to use a custom user name and password validator</span></span>  
  
1. <span data-ttu-id="d0f6b-114">Configure uma associação que usa segurança de mensagem sobre qualquer transporte ou segurança em nível de transporte sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="d0f6b-115">Ao usar a segurança de mensagem, adicione uma das associações fornecidas pelo sistema, como uma [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou um [ \<> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que ofereça suporte à segurança da `UserName` mensagem e ao tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="d0f6b-116">Ao usar a segurança em nível de transporte por http (S), adicione o [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)de [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou BasicHttpBinding, uma [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) de NetTcpBinding ou um [ \<> personalizadobinding ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)que usa http (S) e o `Basic` esquema de autenticação.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d0f6b-117">Quando [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior é usado, você pode usar um validador personalizado de nome de usuário e senha com a segurança de mensagem e transporte.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="d0f6b-118">Com o WinFX, um nome de usuário personalizado e um validador de senha só podem ser usados com a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d0f6b-119">Para obter mais informações sobre \<como usar o > NetTcpBinding neste contexto, consulte [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d0f6b-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1. <span data-ttu-id="d0f6b-120">No arquivo de configuração, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<no elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um elemento bindings >.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2. <span data-ttu-id="d0f6b-121">Adicione um [ \<elemento WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) à seção associações.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="d0f6b-122">Para obter mais informações sobre como criar um elemento de associação [do WCF, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3. <span data-ttu-id="d0f6b-123">Defina o `mode` atributo `Message` `TransportWithMessageCredential` `Transport` [ \<do > de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) como, ou.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
    4. <span data-ttu-id="d0f6b-124">Defina o `clientCredentialType` atributo [ \<do > de mensagens](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<> de transporte](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6b-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="d0f6b-125">Ao usar a segurança da mensagem, `clientCredentialType` defina o atributo [ \<da mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) como. `UserName`</span><span class="sxs-lookup"><span data-stu-id="d0f6b-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="d0f6b-126">Ao usar a `clientCredentialType` segurança em nível `Basic` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) de transporte por http (S), defina o atributo do > de [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) transporte ou do > de transporte como.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d0f6b-127">Quando um serviço WCF é hospedado no serviços de informações da Internet (IIS) usando a segurança em nível de transporte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> e a propriedade é <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>definida como, o esquema de autenticação personalizado usa um subconjunto da autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="d0f6b-128">Isso ocorre porque, nesse cenário, o IIS executa a autenticação do Windows antes do WCF invocando o autenticador personalizado.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="d0f6b-129">Para obter mais informações sobre como criar um elemento de associação [do WCF, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="d0f6b-130">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2. <span data-ttu-id="d0f6b-131">Configure um comportamento que especifica que um validador personalizado de nome de usuário e senha é usado para validar os pares de nome de usuário e senha para tokens de segurança de entrada do <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1. <span data-ttu-id="d0f6b-132">Como um filho para o [ \<elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um [ \<elemento Behaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="d0f6b-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2. <span data-ttu-id="d0f6b-133">Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ >deportaisaoelementocomportamentos>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d0f6b-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3. <span data-ttu-id="d0f6b-134">Adicione um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e defina o `name` atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4. <span data-ttu-id="d0f6b-135">Adicione um [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ao elemento de [ \<> de comportamento](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="d0f6b-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5. <span data-ttu-id="d0f6b-136">Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ >userNameAuthenticationà>ServiceCredentials.\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d0f6b-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6. <span data-ttu-id="d0f6b-137">Defina o `userNamePasswordValidationMode` como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d0f6b-138">Se o `userNamePasswordValidationMode` valor não for definido, o WCF usará a autenticação do Windows em vez do nome de usuário e do validador de senha personalizados.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7. <span data-ttu-id="d0f6b-139">Defina `customUserNamePasswordValidatorType` como o tipo que representa o seu validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="d0f6b-140">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d0f6b-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0f6b-141">Example</span></span>  
 <span data-ttu-id="d0f6b-142">O exemplo de código a seguir demonstra como criar um validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="d0f6b-143">Não use o código que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d0f6b-144">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d0f6b-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d0f6b-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0f6b-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="d0f6b-146">Como: Usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d0f6b-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="d0f6b-147">Autenticação</span><span class="sxs-lookup"><span data-stu-id="d0f6b-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
