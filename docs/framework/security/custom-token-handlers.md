---
title: Manipuladores de token personalizados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d471e860e74c9a01770c95671401bdbbc23643cb
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="custom-token-handlers"></a><span data-ttu-id="e1baa-102">Manipuladores de token personalizados</span><span class="sxs-lookup"><span data-stu-id="e1baa-102">Custom Token Handlers</span></span>
<span data-ttu-id="e1baa-103">Este tópico aborda os manipuladores de token no WIF e como eles são usados para processar tokens.</span><span class="sxs-lookup"><span data-stu-id="e1baa-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="e1baa-104">O tópico também aborda o que é necessário para criar manipuladores de token personalizados para os tipos de token sem suporte por padrão no WIF.</span><span class="sxs-lookup"><span data-stu-id="e1baa-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="e1baa-105">Introdução aos manipuladores de token no WIF</span><span class="sxs-lookup"><span data-stu-id="e1baa-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="e1baa-106">O WIF depende dos manipuladores de token de segurança para criar, ler, gravar e validar tokens para um aplicativo RP (de terceira parte confiável) ou um STS (serviço de token de segurança).</span><span class="sxs-lookup"><span data-stu-id="e1baa-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="e1baa-107">Os manipuladores de token são pontos de extensibilidade para você adicionar um manipulador de token personalizado ao pipeline do WIF ou para personalizar a maneira como um manipulador de token existente gerencia tokens.</span><span class="sxs-lookup"><span data-stu-id="e1baa-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="e1baa-108">O WIF fornece nove manipuladores de token de segurança internos que podem ser modificados ou totalmente substituídos para alterar a funcionalidade, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e1baa-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="e1baa-109">Manipuladores de token de segurança internos no WIF</span><span class="sxs-lookup"><span data-stu-id="e1baa-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="e1baa-110">O WIF 4.5 inclui nove classes de manipulador de token de segurança derivados da classe base abstrata <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="e1baa-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="e1baa-111">Adicionando um Manipulador de Token Personalizado</span><span class="sxs-lookup"><span data-stu-id="e1baa-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="e1baa-112">Alguns tipos de token, como SWT (Tokens Web Simples) e JWT (Tokens Web JSON), não têm manipuladores de token internos fornecidos pelo WIF.</span><span class="sxs-lookup"><span data-stu-id="e1baa-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="e1baa-113">Para esses tipos de token e para outros que não têm um manipulador interno, é necessário executar as etapas a seguir para criar um manipulador de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="e1baa-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="e1baa-114">Adicionando um manipulador de token personalizado</span><span class="sxs-lookup"><span data-stu-id="e1baa-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="e1baa-115">Crie uma nova classe que é derivada de <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="e1baa-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="e1baa-116">Substitua os seguintes métodos e forneça sua própria implementação:</span><span class="sxs-lookup"><span data-stu-id="e1baa-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="e1baa-117">Adicione uma referência ao novo manipulador de token personalizado no arquivo *Web.config* ou *App.config*, na seção **\<system.identityModel>** que se aplica ao WIF.</span><span class="sxs-lookup"><span data-stu-id="e1baa-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="e1baa-118">Por exemplo, a marcação de configuração a seguir especifica um novo manipulador de token chamado **MyCustomTokenHandler** que reside no namespace **CustomToken**.</span><span class="sxs-lookup"><span data-stu-id="e1baa-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="e1baa-119">Observe que, se você fornecer seu próprio manipulador de token para manipular um tipo de token que já tem um manipulador de token interno, precisará adicionar um elemento **\<remove>** para remover o manipulador padrão e, em vez disso, usar o manipulador personalizado.</span><span class="sxs-lookup"><span data-stu-id="e1baa-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="e1baa-120">Por exemplo, a seguinte configuração substitui o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> padrão pelo manipulador de token personalizado:</span><span class="sxs-lookup"><span data-stu-id="e1baa-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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

