---
title: 'Como: usar um validador personalizado de nome de usuário e senha'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 98ffad7e717aac949509fa701c77d8ba2b80a695
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834690"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Como: usar um validador personalizado de nome de usuário e senha

Por padrão, quando um nome de usuário e uma senha são usados para autenticação, Windows Communication Foundation (WCF) usa o Windows para validar o nome de usuário e a senha. No entanto, o WCF permite esquemas de autenticação de senha e nome de usuário personalizados, também conhecidos como *validadores*. Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.

Para obter um aplicativo de exemplo, consulte o [validador de senha do nome de usuário](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Para criar um validador personalizado de nome de usuário e senha

1. Crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Implemente o esquema de autenticação personalizado substituindo o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    Não use o código no exemplo a seguir que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção. Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.

    Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Para configurar um serviço para usar um validador personalizado de nome de usuário e senha

1. Configure uma associação que usa segurança de mensagem sobre qualquer transporte ou segurança em nível de transporte sobre HTTP.

    Ao usar a segurança de mensagem, adicione uma das associações fornecidas pelo sistema, como um [> \<wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou um [> @no__t 3customBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que ofereça suporte à segurança de mensagens e ao tipo de credencial `UserName`.

    Ao usar a segurança em nível de transporte por HTTP (S), adicione o [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), uma @no__t > [-5netTcpBinding](../../configure-apps/file-schema/wcf/nettcpbinding.md) ou uma @no__t [>](../../configure-apps/file-schema/wcf/custombinding.md) que usa http (S) e o esquema de autenticação `Basic`.

    > [!NOTE]
    > Quando [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior é usado, você pode usar um validador personalizado de nome de usuário e senha com a segurança de mensagem e transporte. Com o WinFX, um nome de usuário personalizado e um validador de senha só podem ser usados com a segurança da mensagem.

    > [!TIP]
    > Para obter mais informações sobre como usar o \<netTcpBinding > neste contexto, consulte [\<security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).

    1. No arquivo de configuração, no elemento [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um elemento [> \<bindings](../../configure-apps/file-schema/wcf/bindings.md) .

    2. Adicione um elemento [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) à seção associações. Para obter mais informações sobre como criar um elemento de associação do WCF, consulte [How para: Especifique uma associação de serviço na](../how-to-specify-a-service-binding-in-configuration.md)configuração.

    3. Defina o atributo `mode` do [\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message`, `Transport` ou `TransportWithMessageCredential`.

    4. Defina o atributo `clientCredentialType` do [\<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [\<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).

        Ao usar a segurança da mensagem, defina o atributo `clientCredentialType` do [> \<message](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) como `UserName`.

        Ao usar a segurança em nível de transporte por HTTP (S), defina o atributo `clientCredentialType` do [\<transport >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [\<transport >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) como `Basic`.

        > [!NOTE]
        > Quando um serviço WCF é hospedado no Serviços de Informações da Internet (IIS) usando a segurança em nível de transporte e a propriedade <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> é definida como <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, o esquema de autenticação personalizado usa um subconjunto da autenticação do Windows. Isso ocorre porque, nesse cenário, o IIS executa a autenticação do Windows antes do WCF invocando o autenticador personalizado.

    Para obter mais informações sobre como criar um elemento de associação do WCF, consulte [How para: Especifique uma associação de serviço na](../how-to-specify-a-service-binding-in-configuration.md)configuração.

    O exemplo a seguir mostra o código de configuração para a associação:

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

    1. Como um filho para o elemento [> @no__t. ServiceModel](../../configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um elemento [> \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    2. Adicione um [> \<serviceBehaviors](../../configure-apps/file-schema/wcf/servicebehaviors.md) ao elemento [> \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    3. Adicione um elemento de [> \<behavior](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) e defina o atributo `name` com um valor apropriado.

    4. Adicione um [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) ao elemento [> \<behavior](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    5. Adicione um [> \<userNameAuthentication](../../configure-apps/file-schema/wcf/usernameauthentication.md) ao [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md).

    6. Defina o `userNamePasswordValidationMode` como `Custom`.

        > [!IMPORTANT]
        > Se o valor `userNamePasswordValidationMode` não for definido, o WCF usará a autenticação do Windows em vez do nome de usuário e do validador de senha personalizados.

    7. Defina `customUserNamePasswordValidatorType` como o tipo que representa o seu validador personalizado de nome de usuário e senha.

    O exemplo a seguir mostra o fragmento `<serviceCredentials>` para este ponto:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra como criar um validador personalizado de nome de usuário e senha. Não use o código que substitui o método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> em um ambiente de produção. Substitua o código pelo esquema personalizado de validação de nome de usuário e senha, o que pode envolver recuperar pares de nome de usuário e senha de um banco de dados.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Como: Usar o provedor de associação do ASP.NET @ no__t-0
- [Autenticação](authentication-in-wcf.md)
