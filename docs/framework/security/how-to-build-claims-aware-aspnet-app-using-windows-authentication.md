---
title: Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação do Windows
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a5dbec2e92d32e45bc0271de04f8c6403f67f90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="cd42a-102">Como criar um aplicativo ASP.NET baseado em declarações usando a Autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="cd42a-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="cd42a-103">Applies To</span></span>  
  
-   <span data-ttu-id="cd42a-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="cd42a-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="cd42a-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="cd42a-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="cd42a-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="cd42a-106">Summary</span></span>  
 <span data-ttu-id="cd42a-107">Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET Web Forms simples baseado em declarações que usa a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd42a-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="cd42a-108">Também fornece instruções sobre como testar o aplicativo para verificar se as declarações são apresentadas quando um usuário se conecta usando a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd42a-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="cd42a-109">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="cd42a-109">Contents</span></span>  
  
-   <span data-ttu-id="cd42a-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cd42a-110">Objectives</span></span>  
  
-   <span data-ttu-id="cd42a-111">Visão geral</span><span class="sxs-lookup"><span data-stu-id="cd42a-111">Overview</span></span>  
  
-   <span data-ttu-id="cd42a-112">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="cd42a-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="cd42a-113">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="cd42a-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="cd42a-114">Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="cd42a-115">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="cd42a-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="cd42a-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cd42a-116">Objectives</span></span>  
  
-   <span data-ttu-id="cd42a-117">Configurar um aplicativo ASP.NET Web Forms para declarações usando a autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="cd42a-118">Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente</span><span class="sxs-lookup"><span data-stu-id="cd42a-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cd42a-119">Visão geral</span><span class="sxs-lookup"><span data-stu-id="cd42a-119">Overview</span></span>  
 <span data-ttu-id="cd42a-120">No .NET 4.5, o WIF e sua autorização baseada em declarações foram incluídos como parte integrante do Framework.</span><span class="sxs-lookup"><span data-stu-id="cd42a-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="cd42a-121">Anteriormente, se você quisesse obter declarações de um usuário do ASP.NET, precisava instalar o WIF e, em seguida, converter as interfaces para objetos de Entidade de Segurança, como `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="cd42a-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="cd42a-122">Agora, as declarações são atendidas automaticamente por esses objetos de Entidade de Segurança.</span><span class="sxs-lookup"><span data-stu-id="cd42a-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="cd42a-123">A autenticação do Windows se beneficiou com a inclusão do WIF no .NET 4.5, porque todos os usuários autenticados pelas credenciais do Windows têm declarações associadas a eles automaticamente.</span><span class="sxs-lookup"><span data-stu-id="cd42a-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="cd42a-124">Comece a usar essas declarações imediatamente em um aplicativo ASP.NET que usa a autenticação do Windows, conforme demonstrado por estas Instruções.</span><span class="sxs-lookup"><span data-stu-id="cd42a-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="cd42a-125">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="cd42a-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="cd42a-126">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="cd42a-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="cd42a-127">Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="cd42a-128">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="cd42a-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="cd42a-129">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="cd42a-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="cd42a-130">Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="cd42a-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="cd42a-131">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="cd42a-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="cd42a-132">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, em seguida, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="cd42a-133">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="cd42a-134">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="cd42a-135">Depois que o projeto **TestApp** for criado, clique nele no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="cd42a-136">As propriedades do projeto serão exibidas no painel **Propriedades** abaixo do **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="cd42a-137">Defina a propriedade **Autenticação do Windows** como **Habilitada**.</span><span class="sxs-lookup"><span data-stu-id="cd42a-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="cd42a-138">A autenticação do Windows está desabilitada por padrão em novos aplicativos ASP.NET e, portanto, você deve habilitá-la manualmente.</span><span class="sxs-lookup"><span data-stu-id="cd42a-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="cd42a-139">Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para declarações usando a Autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="cd42a-140">Nesta etapa, você adicionará uma entrada de configuração ao arquivo de configuração *Web.config* e modifique o arquivo *Default.aspx* para exibir as informações de declarações de uma conta.</span><span class="sxs-lookup"><span data-stu-id="cd42a-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="cd42a-141">Para configurar um aplicativo ASP.NET para declarações usando a autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="cd42a-142">No arquivo **Default.aspx** do projeto *TestApp*, substitua a marcação existente pela seguinte:</span><span class="sxs-lookup"><span data-stu-id="cd42a-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
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
  
     <span data-ttu-id="cd42a-143">Essa etapa adiciona um controle GridView à página *Default.aspx* que será populada com as declarações recuperadas da autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd42a-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="cd42a-144">Salve o arquivo *Default.aspx* e, depois, abra seu arquivo code-behind chamado *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="cd42a-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="cd42a-145">Substitua o código existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="cd42a-145">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="cd42a-146">O código acima exibirá as declarações sobre um usuário autenticado.</span><span class="sxs-lookup"><span data-stu-id="cd42a-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="cd42a-147">Para alterar o tipo de autenticação do aplicativo, modifique o bloco **\<authentication>** na seção **\<system.web>** do arquivo *Web.config* da raiz do projeto, de modo que ele inclua somente a seguinte entrada de configuração:</span><span class="sxs-lookup"><span data-stu-id="cd42a-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="cd42a-148">Por fim, modifique o bloco **\<authorization>** na seção **\<system.web>** do mesmo arquivo *Web.config* para forçar a autenticação:</span><span class="sxs-lookup"><span data-stu-id="cd42a-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="cd42a-149">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="cd42a-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="cd42a-150">Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd42a-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="cd42a-151">Para testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cd42a-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="cd42a-152">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cd42a-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="cd42a-153">Você deverá ver *Default.aspx* e o nome de sua conta do Windows (incluindo o nome de domínio) já deverá ser exibido como o usuário autenticado no canto superior direito da página.</span><span class="sxs-lookup"><span data-stu-id="cd42a-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="cd42a-154">O conteúdo da página deverá incluir uma tabela preenchida com as declarações recuperadas de sua conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd42a-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
