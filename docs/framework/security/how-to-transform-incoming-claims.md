---
title: 'Como: transformar declarações de entrada'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041476"
---
# <a name="how-to-transform-incoming-claims"></a>Como: transformar declarações de entrada

## <a name="applies-to"></a>Aplica-se a

- Microsoft® Windows® Identity Foundation (WIF)

- Web Forms do ASP.NET®

## <a name="summary"></a>Resumo

Estas instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo ASP.NET Web Forms simples com reconhecimento de declarações e transformar as declarações de entrada. Elas também fornecem explicações sobre como testar o aplicativo para verificar se as declarações transformadas são apresentadas quando o aplicativo é executado.

## <a name="contents"></a>Conteúdo

- Objetivos

- Visão geral

- Resumo das etapas

- Etapa 1 – criar um aplicativo ASP.NET Web Forms simples

- Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado

- Etapa 3 – Testar a solução

## <a name="objectives"></a>Objetivos

- Configurar um aplicativo ASP.NET Web Forms para autenticação baseada em declarações

- Transformar declarações de entrada com a adição de uma declaração da função de administrador

- Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente

## <a name="overview"></a>Visão geral

O WIF expõe uma classe chamada <xref:System.Security.Claims.ClaimsAuthenticationManager> que permite que os usuários modifiquem declarações antes que elas sejam apresentadas para um aplicativo RP (de terceira parte confiável). O <xref:System.Security.Claims.ClaimsAuthenticationManager> é útil para separação de interesses entre autenticação e o código do aplicativo subjacente. O exemplo a seguir demonstra como adicionar uma função às declarações na <xref:System.Security.Claims.ClaimsPrincipal> de entrada que pode ser necessária para o RP.

## <a name="summary-of-steps"></a>Resumo das etapas

- Etapa 1 – criar um aplicativo ASP.NET Web Forms simples

- Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado

- Etapa 3 – Testar a solução

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples

Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.

#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples

1. Inicie o Visual Studio em modo elevado como administrador.

2. No Visual Studio, clique em **Arquivo**, **Novo** e **Projeto**.

3. Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.

4. Em **Nome**, insira `TestApp` e pressione **OK**.

5. Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.

6. A janela **Identidade e Acesso** é exibida. Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.

7. No arquivo *Default.aspx*, substitua a marcação existente pela seguinte e então salve o arquivo:

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. Abra o arquivo code-behind chamado *Default.aspx.cs*. Substitua o código existente pelo fornecido a seguir e salve o arquivo:

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado

Nesta etapa, você substituirá a funcionalidade padrão na classe <xref:System.Security.Claims.ClaimsAuthenticationManager> para adicionar uma função de administrador à entidade de segurança de entrada.

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado

1. No Visual Studio, clique com o botão direito do mouse na solução, clique em **Adicionar** e **Novo Projeto**.

2. Na janela **Adicionar Novo Projeto**, selecione **Biblioteca de Classes** da lista de modelos do **Visual C#** , digite `ClaimsTransformation` e pressione **OK**. O novo projeto será criado na pasta da solução.

3. Clique com o botão direito do mouse em **Referências**, no projeto **ClaimsTransformation** e em **Adicionar Referência**.

4. Na janela **Gerenciador de Referências**, selecione **System.IdentityModel** e, em seguida, clique em **OK**.

5. Abra **Class1.cs** ou, se ele não existir, clique com o botão direito do mouse em **ClaimsTransformation**, clique em **Adicionar** e, em seguida, clique em **Classe...**

6. Adicione o seguinte usando diretivas no arquivo de código:

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. Adicione a classe e o método a seguir no arquivo de código.

    > [!WARNING]
    > O código a seguir é exclusivamente para fins de demonstração; certifique-se de que você verifica suas permissões pretendidas no código de produção.

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. Salve o arquivo e compile o projeto **ClaimsTransformation**.

9. No seu projeto ASP.NET **TestApp**, clique com o botão direito do mouse em Referências e, em seguida, clique em **Adicionar Referência**.

10. Na janela **Gerenciador de Referências**, selecione **Solução** no menu à esquerda, selecione **ClaimsTransformation** das opções populadas e clique em  **OK**.

11. No arquivo **Web.config** raiz, navegue até a entrada **\<system.identityModel>** . Dentro dos elementos **\<identityConfiguration>** , adicione a linha a seguir e salve o arquivo:

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução

Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação de formulários.

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação de formulários

1. Pressione **F5** para compilar e executar o aplicativo. O *Default.aspx* deverá ser apresentado a você.

2. Na página *Default.aspx*, você deverá ver uma tabela abaixo do cabeçalho **Suas Declarações**, que inclui as informações das declarações **Issuer**, **OriginalIssuer**, **Type**, **Value** e **ValueType** sobre a sua conta. A última linha deve ser apresentada da seguinte maneira:

    ||||||
    |-|-|-|-|-|
    |LOCAL AUTHORITY|LOCAL AUTHORITY|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|Admin|<https://www.w3.org/2001/XMLSchema#string>|
