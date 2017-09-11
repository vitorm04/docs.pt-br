---
title: "Como transformar declarações de entrada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="db4e2-102">Como transformar declarações de entrada</span><span class="sxs-lookup"><span data-stu-id="db4e2-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="db4e2-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="db4e2-103">Applies To</span></span>  
  
-   <span data-ttu-id="db4e2-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="db4e2-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="db4e2-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="db4e2-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="db4e2-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="db4e2-106">Summary</span></span>  
 <span data-ttu-id="db4e2-107">Estas instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo ASP.NET Web Forms simples com reconhecimento de declarações e transformar as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="db4e2-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="db4e2-108">Elas também fornecem explicações sobre como testar o aplicativo para verificar se as declarações transformadas são apresentadas quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="db4e2-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="db4e2-109">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="db4e2-109">Contents</span></span>  
  
-   <span data-ttu-id="db4e2-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db4e2-110">Objectives</span></span>  
  
-   <span data-ttu-id="db4e2-111">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="db4e2-111">Overview</span></span>  
  
-   <span data-ttu-id="db4e2-112">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="db4e2-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="db4e2-113">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="db4e2-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="db4e2-114">Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado</span><span class="sxs-lookup"><span data-stu-id="db4e2-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="db4e2-115">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="db4e2-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="db4e2-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db4e2-116">Objectives</span></span>  
  
-   <span data-ttu-id="db4e2-117">Configurar um aplicativo ASP.NET Web Forms para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="db4e2-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="db4e2-118">Transformar declarações de entrada com a adição de uma declaração da função de administrador</span><span class="sxs-lookup"><span data-stu-id="db4e2-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="db4e2-119">Testar o aplicativo ASP.NET Web Forms para ver se ele está funcionando corretamente</span><span class="sxs-lookup"><span data-stu-id="db4e2-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="db4e2-120">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="db4e2-120">Overview</span></span>  
 <span data-ttu-id="db4e2-121">O WIF expõe uma classe chamada <xref:System.Security.Claims.ClaimsAuthenticationManager> que permite que os usuários modifiquem declarações antes que elas sejam apresentadas para um aplicativo RP (de terceira parte confiável).</span><span class="sxs-lookup"><span data-stu-id="db4e2-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="db4e2-122">O <xref:System.Security.Claims.ClaimsAuthenticationManager> é útil para separação de interesses entre autenticação e o código do aplicativo subjacente.</span><span class="sxs-lookup"><span data-stu-id="db4e2-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="db4e2-123">O exemplo a seguir demonstra como adicionar uma função às declarações na <xref:System.Security.Claims.ClaimsPrincipal> de entrada que pode ser necessária para o RP.</span><span class="sxs-lookup"><span data-stu-id="db4e2-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="db4e2-124">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="db4e2-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="db4e2-125">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="db4e2-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="db4e2-126">Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado</span><span class="sxs-lookup"><span data-stu-id="db4e2-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="db4e2-127">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="db4e2-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="db4e2-128">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples</span><span class="sxs-lookup"><span data-stu-id="db4e2-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="db4e2-129">Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="db4e2-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="db4e2-130">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="db4e2-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="db4e2-131">Inicie o Visual Studio em modo elevado como administrador.</span><span class="sxs-lookup"><span data-stu-id="db4e2-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="db4e2-132">No Visual Studio, clique em **Arquivo**, **Novo** e **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="db4e2-133">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="db4e2-134">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="db4e2-135">Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="db4e2-136">A janela **Identidade e Acesso** é exibida.</span><span class="sxs-lookup"><span data-stu-id="db4e2-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="db4e2-137">Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="db4e2-138">No arquivo *Default.aspx*, substitua a marcação existente pela seguinte e então salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="db4e2-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
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
  
8.  <span data-ttu-id="db4e2-139">Abra o arquivo code-behind chamado *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="db4e2-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="db4e2-140">Substitua o código existente pelo fornecido a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="db4e2-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="db4e2-141">Etapa 2 – implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado</span><span class="sxs-lookup"><span data-stu-id="db4e2-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="db4e2-142">Nesta etapa, você substituirá a funcionalidade padrão na classe <xref:System.Security.Claims.ClaimsAuthenticationManager> para adicionar uma função de administrador à entidade de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="db4e2-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="db4e2-143">Implementar a transformação de declarações usando um ClaimsAuthenticationManager personalizado</span><span class="sxs-lookup"><span data-stu-id="db4e2-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="db4e2-144">No Visual Studio, clique com o botão direito do mouse na solução, clique em **Adicionar** e **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="db4e2-145">Na janela **Adicionar Novo Projeto**, selecione **Biblioteca de Classes** da lista de modelos do **Visual C#**, digite `ClaimsTransformation` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="db4e2-146">O novo projeto será criado na pasta da solução.</span><span class="sxs-lookup"><span data-stu-id="db4e2-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="db4e2-147">Clique com o botão direito do mouse em **Referências**, no projeto **ClaimsTransformation** e em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="db4e2-148">Na janela **Gerenciador de Referências**, selecione **System.IdentityModel** e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="db4e2-149">Abra **Class1.cs** ou, se ele não existir, clique com o botão direito do mouse em **ClaimsTransformation**, clique em **Adicionar** e, em seguida, clique em **Classe...**</span><span class="sxs-lookup"><span data-stu-id="db4e2-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="db4e2-150">Adicione o seguinte usando diretivas no arquivo de código:</span><span class="sxs-lookup"><span data-stu-id="db4e2-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="db4e2-151">Adicione a classe e o método a seguir no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="db4e2-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="db4e2-152">O código a seguir é exclusivamente para fins de demonstração; certifique-se de que você verifica suas permissões pretendidas no código de produção.</span><span class="sxs-lookup"><span data-stu-id="db4e2-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
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
  
8.  <span data-ttu-id="db4e2-153">Salve o arquivo e compile o projeto **ClaimsTransformation**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="db4e2-154">No seu projeto ASP.NET **TestApp**, clique com o botão direito do mouse em Referências e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="db4e2-155">Na janela **Gerenciador de Referências**, selecione **Solução** no menu à esquerda, selecione **ClaimsTransformation** das opções populadas e clique em  **OK**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="db4e2-156">No arquivo **Web.config** raiz, navegue até a entrada **\<system.identityModel>**.</span><span class="sxs-lookup"><span data-stu-id="db4e2-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="db4e2-157">Dentro dos elementos **\<identityConfiguration>**, adicione a linha a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="db4e2-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="db4e2-158">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="db4e2-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="db4e2-159">Nesta etapa, você testará o aplicativo ASP.NET Web Forms e verificará se as declarações são apresentadas quando um usuário entra com a autenticação de formulários.</span><span class="sxs-lookup"><span data-stu-id="db4e2-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="db4e2-160">Testar o aplicativo ASP.NET Web Forms para declarações usando a autenticação de formulários</span><span class="sxs-lookup"><span data-stu-id="db4e2-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="db4e2-161">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db4e2-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="db4e2-162">O *Default.aspx* deverá ser apresentado a você.</span><span class="sxs-lookup"><span data-stu-id="db4e2-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="db4e2-163">Na página *Default.aspx*, você deverá ver uma tabela abaixo do cabeçalho **Suas Declarações**, que inclui as informações das declarações **Issuer**, **OriginalIssuer**, **Type**, **Value** e **ValueType** sobre a sua conta.</span><span class="sxs-lookup"><span data-stu-id="db4e2-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="db4e2-164">A última linha deve ser apresentada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db4e2-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="db4e2-165">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="db4e2-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="db4e2-166">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="db4e2-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="db4e2-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="db4e2-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="db4e2-168">Admin</span><span class="sxs-lookup"><span data-stu-id="db4e2-168">Admin</span></span>|<span data-ttu-id="db4e2-169">http://www.w3.org/2001/XMLSchema#string</span><span class="sxs-lookup"><span data-stu-id="db4e2-169">http://www.w3.org/2001/XMLSchema#string</span></span>|

