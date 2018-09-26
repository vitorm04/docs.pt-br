---
title: Manipuladores de token personalizados
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: c27abb5df7f895a9dec5f7f784f1a3ff0b31edb7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200874"
---
# <a name="custom-token-handlers"></a>Manipuladores de token personalizados
Este tópico aborda os manipuladores de token no WIF e como eles são usados para processar tokens. O tópico também aborda o que é necessário para criar manipuladores de token personalizados para os tipos de token sem suporte por padrão no WIF.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Introdução aos manipuladores de token no WIF  
 O WIF depende dos manipuladores de token de segurança para criar, ler, gravar e validar tokens para um aplicativo RP (de terceira parte confiável) ou um STS (serviço de token de segurança). Os manipuladores de token são pontos de extensibilidade para você adicionar um manipulador de token personalizado ao pipeline do WIF ou para personalizar a maneira como um manipulador de token existente gerencia tokens. O WIF fornece nove manipuladores de token de segurança internos que podem ser modificados ou totalmente substituídos para alterar a funcionalidade, conforme necessário.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Manipuladores de token de segurança internos no WIF  
 O WIF 4.5 inclui nove classes de manipulador de token de segurança derivados da classe base abstrata <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Adicionando um Manipulador de Token Personalizado  
 Alguns tipos de token, como SWT (Tokens Web Simples) e JWT (Tokens Web JSON), não têm manipuladores de token internos fornecidos pelo WIF. Para esses tipos de token e para outros que não têm um manipulador interno, é necessário executar as etapas a seguir para criar um manipulador de token personalizado.  
  
#### <a name="adding-a-custom-token-handler"></a>Adicionando um manipulador de token personalizado  
  
1.  Crie uma nova classe que é derivada de <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Substitua os seguintes métodos e forneça sua própria implementação:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Adicione uma referência ao novo manipulador de token personalizado no arquivo *Web.config* ou *App.config*, na seção **\<system.identityModel>** que se aplica ao WIF. Por exemplo, a marcação de configuração a seguir especifica um novo manipulador de token chamado **MyCustomTokenHandler** que reside no namespace **CustomToken**.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Observe que, se você fornecer seu próprio manipulador de token para manipular um tipo de token que já tem um manipulador de token interno, precisará adicionar um elemento **\<remove>** para remover o manipulador padrão e, em vez disso, usar o manipulador personalizado. Por exemplo, a seguinte configuração substitui o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> padrão pelo manipulador de token personalizado:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
