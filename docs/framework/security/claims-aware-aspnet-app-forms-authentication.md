---
title: Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação Baseada em Formulários
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025526"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação Baseada em Formulários
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET Web Forms simples baseado em declarações que usa a autenticação de Formulários. Também fornece instruções sobre como testar o aplicativo para verificar se as declarações são apresentadas quando um usuário se conecta usando a autenticação de Formulários.  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Visão geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários  
  
-   Etapa 3 – Testar a solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Configurar um aplicativo ASP.NET Web Forms para declarações usando a autenticação de Formulários  
  
-   Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente  
  
## <a name="overview"></a>Visão geral  
 No .NET 4.5, o WIF e sua autorização baseada em declarações foram incluídos como parte integrante do Framework. Anteriormente, se você quisesse obter declarações de um usuário do ASP.NET, precisava instalar o WIF e, em seguida, converter as interfaces para objetos de Entidade de Segurança, como `Thread.CurrentPrincipal` ou `HttpContext.Current.User`. Agora, as declarações são atendidas automaticamente por esses objetos de Entidade de Segurança.  
  
 A autenticação de Formulários se beneficiou com a inclusão do WIF no .NET 4.5, porque todos os usuários autenticados pelas credenciais de Formulários têm declarações associadas a eles automaticamente. Comece a usar essas declarações imediatamente em um aplicativo ASP.NET que usa a autenticação de Formulários, conforme demonstrado por estas Instruções.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários  
  
-   Etapa 3 – Testar a solução  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
 Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Etapa 2 – Configurar o aplicativo ASP.NET Web Forms para declarações usando a Autenticação de Formulários  
 Nesta etapa, você adicionará uma entrada de configuração ao arquivo de configuração *Web.config* e edite o arquivo *Default.aspx* para exibir as informações de declarações de uma conta.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Para configurar um aplicativo ASP.NET para declarações usando a autenticação de Formulários  
  
1.  No arquivo *Default.aspx*, substitua a marcação existente pela seguinte:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
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
  
     Essa etapa adiciona um controle GridView à página *Default.aspx* que será populada com as declarações recuperadas da autenticação de Formulários.  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     O código acima exibirá declarações sobre um usuário autenticado, incluindo os usuários identificados pela autenticação de Formulários.  
  
## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução  
 Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação de formulários.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação de formulários  
  
1.  Pressione **F5** para compilar e executar o aplicativo. Você deverá ver o *Default.aspx*, que tem os links **Registrar** e **Fazer logon** na parte superior direita da página. Clique em **Registrar**.  
  
2.  Na página **Registrar**, crie uma conta de usuário e, em seguida, clique em **Registrar**. Sua conta será criada usando a autenticação de Formulários e você será conectado automaticamente.  
  
3.  Depois de ser redirecionado para a home page, você deverá ver uma tabela abaixo do cabeçalho **Suas Declarações**, que inclui as informações das declarações **Issuer**, **OriginalIssuer**, **Type**, **Value** e **ValueType** sobre sua conta.
