---
title: 'Como: usar um validador personalizado de nome de usuário e senha'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ad53700590c3f3683663d306e15fcbe857f625e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038994"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Como: usar um validador personalizado de nome de usuário e senha
Por padrão, quando um nome de usuário e senha é usada para autenticação, o Windows Communication Foundation (WCF) usa Windows para validar o nome de usuário e senha. No entanto, WCF permite esquemas de autenticação de nome e a senha da usuário personalizada, também conhecido como *validadores*. Para inserir um validador personalizado de nome de usuário e senha, crie uma classe que deriva de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configure-a.  
  
 Para um aplicativo de exemplo, consulte [validador de senha do nome de usuário](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
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
  
     Ao usar a segurança de mensagem, adicione uma das associações fornecidas pelo sistema, como um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que dá suporte a segurança da mensagem e o `UserName` o tipo de credencial.  
  
     Ao usar a segurança em nível de transporte sobre HTTP (S), adicione a [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), um [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) que usa HTTP (S) e o `Basic` esquema de autenticação.  
  
    > [!NOTE]
    >  Quando [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior é usado, você pode usar um validador personalizado de nome de usuário e senha com a segurança de mensagem e transporte. Com o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], um validador personalizado de nome de usuário e senha só pode ser usado com segurança da mensagem.  
  
    > [!TIP]
    >  Para obter mais informações sobre como usar \<netTcpBinding > neste contexto, consulte [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.  
  
    2. Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento à seção de associações. Para obter mais informações sobre a criação de um elemento de associação do WCF, consulte [como: Especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3. Defina as `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message`, `Transport`, ou `TransportWithMessageCredential`.  
  
    4. Definir o `clientCredentialType` atributo o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Ao usar a segurança de mensagem, defina a `clientCredentialType` atributo o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) para `UserName`.  
  
         Ao usar a segurança em nível de transporte sobre HTTP (S), defina a `clientCredentialType` atributo o [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [ \<transporte >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) para `Basic`.  
  
        > [!NOTE]
        >  Quando um serviço WCF é hospedado no Internet Information Services (IIS) usando a segurança de nível de transporte e o <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> estiver definida como <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, o esquema de autenticação personalizada usa um subconjunto de autenticação do Windows. Isso ocorre porque, nesse cenário, o IIS executa autenticação do Windows antes de chamar o autenticador personalizado do WCF.  
  
     Para obter mais informações sobre a criação de um elemento de associação do WCF, consulte [como: Especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
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
  
    1. Como um filho para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
    2. Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.  
  
    3. Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.  
  
    4. Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento.  
  
    5. Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6. Defina o `userNamePasswordValidationMode` como `Custom`.  
  
        > [!IMPORTANT]
        >  Se o `userNamePasswordValidationMode` valor não for definido, o WCF usa a autenticação do Windows em vez do validador de nome e a senha do usuário personalizada.  
  
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
