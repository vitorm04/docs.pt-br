---
title: 'Como: usar um validador personalizado de nome de usuário e senha'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7df6ec57204990066ce59700e5c2582701f2a81a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045908"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Como: usar um validador personalizado de nome de usuário e senha

Por padrão, quando um nome de usuário e uma senha são usados para autenticação, Windows Communication Foundation (WCF) usa o Windows para validar o nome de usuário e a senha. No entanto, o WCF permite esquemas de autenticação de senha e nome de usuáriopersonalizados, também conhecidos como validadores. Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.

Para obter um aplicativo de exemplo, consulte o validador de [senha do nome de usuário](../../../../docs/framework/wcf/samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Para criar um validador personalizado de nome de usuário e senha

1. Crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Implemente o esquema de autenticação personalizado substituindo o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    Não use o código no exemplo a seguir que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção. Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.

    Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Para configurar um serviço para usar um validador personalizado de nome de usuário e senha

1. Configure uma associação que usa segurança de mensagem sobre qualquer transporte ou segurança em nível de transporte sobre HTTP.

    Ao usar a segurança de mensagem, adicione uma das associações fornecidas pelo sistema, como uma [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou um [ \<> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que ofereça suporte à segurança da `UserName` mensagem e ao tipo de credencial.

    Ao usar a segurança em nível de transporte por http (S), adicione o [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)de [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou BasicHttpBinding, uma [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) de NetTcpBinding ou um [ \<> personalizadobinding ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)que usa http (S) e o `Basic` esquema de autenticação.

    > [!NOTE]
    > Quando [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior é usado, você pode usar um validador personalizado de nome de usuário e senha com a segurança de mensagem e transporte. Com o WinFX, um nome de usuário personalizado e um validador de senha só podem ser usados com a segurança da mensagem.

    > [!TIP]
    > Para obter mais informações sobre \<como usar o > NetTcpBinding neste contexto, consulte [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)

    1. No arquivo de configuração, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<no elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um elemento bindings >.

    2. Adicione um [ \<elemento WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) à seção associações. Para obter mais informações sobre como criar um elemento de associação [do WCF, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.

    3. Defina o `mode` atributo `Message` `TransportWithMessageCredential` `Transport` [ \<do > de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) como, ou.

    4. Defina o `clientCredentialType` atributo [ \<do > de mensagens](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<> de transporte](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).

        Ao usar a segurança da mensagem, `clientCredentialType` defina o atributo [ \<da mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) como. `UserName`

        Ao usar a `clientCredentialType` segurança em nível `Basic` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) de transporte por http (S), defina o atributo do > de [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) transporte ou do > de transporte como.

        > [!NOTE]
        > Quando um serviço WCF é hospedado no serviços de informações da Internet (IIS) usando a segurança em nível de transporte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> e a propriedade é <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>definida como, o esquema de autenticação personalizado usa um subconjunto da autenticação do Windows. Isso ocorre porque, nesse cenário, o IIS executa a autenticação do Windows antes do WCF invocando o autenticador personalizado.

    Para obter mais informações sobre como criar um elemento de associação [do WCF, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.

    O exemplo a seguir mostra o código de configuração para a associação.

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

2. Configure um comportamento que especifica que um validador personalizado de nome de usuário e senha é usado para validar os pares de nome de usuário e senha para tokens de segurança de entrada do <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.

    1. Como um filho para o [ \<elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um [ \<elemento Behaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .

    2. Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ >deportaisaoelementocomportamentos>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

    3. Adicione um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e defina o `name` atributo para um valor apropriado.

    4. Adicione um [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ao elemento de [ \<> de comportamento](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    5. Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ >userNameAuthenticationà>ServiceCredentials.\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)

    6. Defina o `userNamePasswordValidationMode` como `Custom`.

        > [!IMPORTANT]
        > Se o `userNamePasswordValidationMode` valor não for definido, o WCF usará a autenticação do Windows em vez do nome de usuário e do validador de senha personalizados.

    7. Defina `customUserNamePasswordValidatorType` como o tipo que representa o seu validador personalizado de nome de usuário e senha.

    O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra como criar um validador personalizado de nome de usuário e senha. Não use o código que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção. Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Como: Usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
