---
title: Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação do Windows
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 2c7877c452c729b30029cad1a8e17600f3dc9661
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198522"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação do Windows
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET Web Forms simples baseado em declarações que usa a autenticação do Windows. Também fornece instruções sobre como testar o aplicativo para verificar se as declarações são apresentadas quando um usuário se conecta usando a autenticação do Windows.  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Visão geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows  
  
-   Etapa 3 – Testar a solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Configurar um aplicativo ASP.NET Web Forms para declarações usando a autenticação do Windows  
  
-   Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente  
  
## <a name="overview"></a>Visão geral  
 No .NET 4.5, o WIF e sua autorização baseada em declarações foram incluídos como parte integrante do Framework. Anteriormente, se você quisesse obter declarações de um usuário do ASP.NET, precisava instalar o WIF e, em seguida, converter as interfaces para objetos de Entidade de Segurança, como `Thread.CurrentPrincipal` ou `HttpContext.Current.User`. Agora, as declarações são atendidas automaticamente por esses objetos de Entidade de Segurança.  
  
 A autenticação do Windows se beneficiou com a inclusão do WIF no .NET 4.5, porque todos os usuários autenticados pelas credenciais do Windows têm declarações associadas a eles automaticamente. Comece a usar essas declarações imediatamente em um aplicativo ASP.NET que usa a autenticação do Windows, conforme demonstrado por estas Instruções.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows  
  
-   Etapa 3 – Testar a solução  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
 Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, em seguida, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
4.  Depois que o projeto **TestApp** for criado, clique nele no **Gerenciador de Soluções**. As propriedades do projeto serão exibidas no painel **Propriedades** abaixo do **Gerenciador de Soluções**. Defina a propriedade **Autenticação do Windows** como **Habilitada**.  
  
    > [!WARNING]
    >  A autenticação do Windows está desabilitada por padrão em novos aplicativos ASP.NET e, portanto, você deve habilitá-la manualmente.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows  
 Nesta etapa, você adicionará uma entrada de configuração ao arquivo de configuração *Web.config* e modifique o arquivo *Default.aspx* para exibir as informações de declarações de uma conta.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Para configurar um aplicativo ASP.NET para declarações usando a autenticação do Windows  
  
1.  No arquivo **Default.aspx** do projeto *TestApp*, substitua a marcação existente pela seguinte:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     Essa etapa adiciona um controle GridView à página *Default.aspx* que será populada com as declarações recuperadas da autenticação do Windows.  
  
2.  Salve o arquivo *Default.aspx* e, depois, abra seu arquivo code-behind chamado *Default.aspx.cs*. Substitua o código existente pelo seguinte:  
  
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
  
     O código acima exibirá as declarações sobre um usuário autenticado.  
  
3.  Para alterar o tipo de autenticação do aplicativo, modifique o bloco **\<authentication>** na seção **\<system.web>** do arquivo *Web.config* da raiz do projeto, de modo que ele inclua somente a seguinte entrada de configuração:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  Por fim, modifique o bloco **\<authorization>** na seção **\<system.web>** do mesmo arquivo *Web.config* para forçar a autenticação:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução  
 Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação do Windows.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Para testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação do Windows  
  
1.  Pressione **F5** para compilar e executar o aplicativo. Você deverá ver *Default.aspx* e o nome de sua conta do Windows (incluindo o nome de domínio) já deverá ser exibido como o usuário autenticado no canto superior direito da página. O conteúdo da página deverá incluir uma tabela preenchida com as declarações recuperadas de sua conta do Windows.
