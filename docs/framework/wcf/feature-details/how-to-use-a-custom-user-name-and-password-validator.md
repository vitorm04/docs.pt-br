---
title: Como usar um validador personalizado de nome de usuário e senha
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601173"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="c7c30-102">Como usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="c7c30-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="c7c30-103">Por padrão, quando um nome de usuário e uma senha são usados para autenticação, Windows Communication Foundation (WCF) usa o Windows para validar o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="c7c30-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="c7c30-104">No entanto, o WCF permite esquemas de autenticação de senha e nome de usuário personalizados, também conhecidos como *validadores*.</span><span class="sxs-lookup"><span data-stu-id="c7c30-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="c7c30-105">Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.</span><span class="sxs-lookup"><span data-stu-id="c7c30-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="c7c30-106">Para obter um aplicativo de exemplo, consulte o [validador de senha do nome de usuário](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="c7c30-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="c7c30-107">Para criar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="c7c30-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="c7c30-108">Crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="c7c30-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="c7c30-109">Implemente o esquema de autenticação personalizado substituindo o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7c30-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="c7c30-110">Não use o código no exemplo a seguir que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="c7c30-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="c7c30-111">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c7c30-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="c7c30-112">Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7c30-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="c7c30-113">Para configurar um serviço para usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="c7c30-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="c7c30-114">Configure uma associação que usa segurança de mensagem sobre qualquer transporte ou segurança em nível de transporte sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7c30-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="c7c30-115">Ao usar a segurança da mensagem, adicione uma das associações fornecidas pelo sistema, como um [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , ou um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) que dê suporte à segurança da mensagem e ao `UserName` tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="c7c30-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="c7c30-116">Ao usar a segurança em nível de transporte por HTTP (S), adicione o [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , um [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) ou um [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) que usa http (s) e o esquema de `Basic` autenticação.</span><span class="sxs-lookup"><span data-stu-id="c7c30-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c7c30-117">Ao usar o .NET Framework 3,5 ou versões posteriores, você pode usar um validador de nome de usuário e senha personalizados com segurança de mensagens e transporte.</span><span class="sxs-lookup"><span data-stu-id="c7c30-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="c7c30-118">Com o WinFX, um nome de usuário personalizado e um validador de senha só podem ser usados com a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c7c30-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="c7c30-119">Para obter mais informações sobre como usar \<netTcpBinding> esse contexto, consulte [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c7c30-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="c7c30-120">No arquivo de configuração, no [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicione um [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c7c30-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="c7c30-121">Adicione um [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) elemento ou à seção de associações.</span><span class="sxs-lookup"><span data-stu-id="c7c30-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="c7c30-122">Para obter mais informações sobre como criar um elemento de associação do WCF, consulte [como especificar uma associação de serviço na configuração](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c7c30-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="c7c30-123">Defina o `mode` atributo de [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message` , `Transport` ou `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="c7c30-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="c7c30-124">Defina o `clientCredentialType` atributo do [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c7c30-124">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="c7c30-125">Ao usar a segurança da mensagem, defina o `clientCredentialType` atributo do [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) para `UserName` .</span><span class="sxs-lookup"><span data-stu-id="c7c30-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="c7c30-126">Ao usar a segurança em nível de transporte por HTTP (S), defina o `clientCredentialType` atributo de [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) para `Basic` .</span><span class="sxs-lookup"><span data-stu-id="c7c30-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="c7c30-127">Quando um serviço WCF é hospedado no Serviços de Informações da Internet (IIS) usando a segurança em nível de transporte e a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> propriedade é definida como <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , o esquema de autenticação personalizado usa um subconjunto da autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c7c30-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="c7c30-128">Isso ocorre porque, nesse cenário, o IIS executa a autenticação do Windows antes do WCF invocando o autenticador personalizado.</span><span class="sxs-lookup"><span data-stu-id="c7c30-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="c7c30-129">Para obter mais informações sobre como criar um elemento de associação do WCF, consulte [como especificar uma associação de serviço na configuração](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c7c30-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="c7c30-130">O exemplo a seguir mostra o código de configuração para a associação:</span><span class="sxs-lookup"><span data-stu-id="c7c30-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="c7c30-131">Configure um comportamento que especifica que um validador personalizado de nome de usuário e senha é usado para validar os pares de nome de usuário e senha para tokens de segurança de entrada do <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="c7c30-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="c7c30-132">Como um filho para o [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicione um [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c7c30-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="c7c30-133">Adicione um [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) ao [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c7c30-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="c7c30-134">Adicione um [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e defina o `name` atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="c7c30-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="c7c30-135">Adicione um [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) ao [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c7c30-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="c7c30-136">Adicione um [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) ao [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="c7c30-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="c7c30-137">Defina o `userNamePasswordValidationMode` para `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c7c30-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="c7c30-138">Se o `userNamePasswordValidationMode` valor não for definido, o WCF usará a autenticação do Windows em vez do nome de usuário e do validador de senha personalizados.</span><span class="sxs-lookup"><span data-stu-id="c7c30-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="c7c30-139">Defina `customUserNamePasswordValidatorType` como o tipo que representa o seu validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="c7c30-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="c7c30-140">O exemplo a seguir mostra o `<serviceCredentials>` fragmento para este ponto:</span><span class="sxs-lookup"><span data-stu-id="c7c30-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="c7c30-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7c30-141">Example</span></span>

<span data-ttu-id="c7c30-142">O exemplo de código a seguir demonstra como criar um validador personalizado de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="c7c30-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="c7c30-143">Não use o código que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="c7c30-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="c7c30-144">Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c7c30-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c7c30-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7c30-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="c7c30-146">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7c30-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="c7c30-147">Autenticação</span><span class="sxs-lookup"><span data-stu-id="c7c30-147">Authentication</span></span>](authentication-in-wcf.md)
