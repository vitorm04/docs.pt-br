---
title: 'Como: criar um aplicativo Web ASP.NET MVC baseado em declarações usando o WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 04861b8c3f2673a5cd093be1351928b1da487147
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335661"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="87a27-102">Como: criar um aplicativo Web ASP.NET MVC baseado em declarações usando o WIF</span><span class="sxs-lookup"><span data-stu-id="87a27-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="87a27-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="87a27-103">Applies To</span></span>  
  
-   <span data-ttu-id="87a27-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="87a27-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="87a27-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="87a27-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="87a27-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="87a27-106">Summary</span></span>  
 <span data-ttu-id="87a27-107">Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET MVC simples baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="87a27-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="87a27-108">Também fornecem instruções sobre como testar o aplicativo Web ASP.NET MVC simples baseado em declarações para uma implementação bem-sucedida da autenticação baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="87a27-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="87a27-109">Estas Instruções não contêm instruções detalhadas para a criação de um STS (Serviço de Token de Segurança) e pressupõe que você já tenha configurado um.</span><span class="sxs-lookup"><span data-stu-id="87a27-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="87a27-110">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="87a27-110">Contents</span></span>  
  
-   <span data-ttu-id="87a27-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87a27-111">Objectives</span></span>  
  
-   <span data-ttu-id="87a27-112">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="87a27-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="87a27-113">Etapa 1 – Criar um aplicativo ASP.NET MVC simples</span><span class="sxs-lookup"><span data-stu-id="87a27-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="87a27-114">Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="87a27-115">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="87a27-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="87a27-116">Itens relacionados</span><span class="sxs-lookup"><span data-stu-id="87a27-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="87a27-117">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87a27-117">Objectives</span></span>  
  
-   <span data-ttu-id="87a27-118">Configurar um aplicativo Web ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="87a27-119">Testar um aplicativo Web ASP.NET MVC bem-sucedido baseado em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="87a27-120">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="87a27-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="87a27-121">Etapa 1 – Criar um aplicativo ASP.NET MVC simples</span><span class="sxs-lookup"><span data-stu-id="87a27-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="87a27-122">Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="87a27-123">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="87a27-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="87a27-124">Etapa 1 – Criar um aplicativo ASP.NET MVC simples</span><span class="sxs-lookup"><span data-stu-id="87a27-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="87a27-125">Nesta etapa, você criará um novo aplicativo ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="87a27-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="87a27-126">Para criar um aplicativo ASP.NET MVC simples</span><span class="sxs-lookup"><span data-stu-id="87a27-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="87a27-127">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="87a27-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="87a27-128">Na janela **Novo Projeto**, clique em **Aplicativo Web ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="87a27-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="87a27-129">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="87a27-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="87a27-130">Na caixa de diálogo **Novo Projeto ASP.NET MVC 3**, selecione **Aplicativo da Internet** nos modelos disponíveis, verifique se o **Mecanismo de Exibição** está definido como **Razor** e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="87a27-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="87a27-131">Quando o novo projeto for aberto, clique com o botão direito do mouse no projeto **TestApp** no **Gerenciador de Soluções** e selecione a opção **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="87a27-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="87a27-132">Na página de propriedades do projeto, clique na guia **Web** à esquerda e verifique se a opção **Usar Servidor Web do IIS Local** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="87a27-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="87a27-133">Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="87a27-134">Nesta etapa, você adicionará entradas de configuração ao arquivo de configuração *Web.config* do aplicativo Web ASP.NET MVC para torná-lo baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="87a27-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="87a27-135">Para configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="87a27-136">Adicione as definições de seção de configuração a seguir ao arquivo de configuração *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="87a27-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="87a27-137">Elas definem as seções de configuração exigidas pelo Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="87a27-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="87a27-138">Adicione as definições imediatamente após o elemento de abertura **\<configuration>**:</span><span class="sxs-lookup"><span data-stu-id="87a27-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="87a27-139">Adicione um elemento **\<location>** que habilita o acesso aos metadados de federação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="87a27-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="87a27-140">Adicione as seguintes entradas de configuração nos elementos **\<system.web>** para negar usuários, desabilitar a autenticação nativa e permitir que o WIF gerencie a autenticação.</span><span class="sxs-lookup"><span data-stu-id="87a27-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="87a27-141">Adicione as entradas de configuração relacionadas ao Windows Identity Foundation a seguir e garanta que a URL e o número da porta do aplicativo ASP.NET correspondam aos valores na entrada **\<audienceUris>**, no atributo **realm** do elemento **\<wsFederation>** e no atributo **reply** do elemento **\<wsFederation>**.</span><span class="sxs-lookup"><span data-stu-id="87a27-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="87a27-142">Também garanta que o valor **issuer** se ajuste à URL do STS (Serviço de Token de Segurança).</span><span class="sxs-lookup"><span data-stu-id="87a27-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <span data-ttu-id="87a27-143">Adicione uma referência ao assembly <xref:System.IdentityModel>.</span><span class="sxs-lookup"><span data-stu-id="87a27-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="87a27-144">Compile a solução para verificar se há erros.</span><span class="sxs-lookup"><span data-stu-id="87a27-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="87a27-145">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="87a27-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="87a27-146">Nesta etapa, você testará o aplicativo Web ASP.NET MVC configurado para a autenticação baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="87a27-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="87a27-147">Para executar um teste básico, você adicionará um código simples que exibe as declarações no token emitido pelo STS (Serviço de Token de Segurança).</span><span class="sxs-lookup"><span data-stu-id="87a27-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="87a27-148">Para testar o aplicativo ASP.NET MVC para autenticação baseada em declarações</span><span class="sxs-lookup"><span data-stu-id="87a27-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="87a27-149">No **Gerenciador de Soluções**, expanda a pasta **Controladores** e abra o arquivo *HomeController.cs* no editor.</span><span class="sxs-lookup"><span data-stu-id="87a27-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="87a27-150">Adicione o seguinte código ao método **Index**:</span><span class="sxs-lookup"><span data-stu-id="87a27-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="87a27-151">No **Gerenciador de Soluções**, expanda **Exibições** e, em seguida, as pastas **Página Inicial** e abra o arquivo *Index.cshtml* no editor.</span><span class="sxs-lookup"><span data-stu-id="87a27-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="87a27-152">Exclua seu conteúdo e adicione a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="87a27-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. <span data-ttu-id="87a27-153">Execute a solução pressionando a tecla **F5**.</span><span class="sxs-lookup"><span data-stu-id="87a27-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="87a27-154">Você deverá ver a página que exibe as declarações no token que foi emitido por você pelo Serviço de Token de Segurança.</span><span class="sxs-lookup"><span data-stu-id="87a27-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="87a27-155">Itens relacionados</span><span class="sxs-lookup"><span data-stu-id="87a27-155">Related Items</span></span>  
  
-   [<span data-ttu-id="87a27-156">Como: criar um aplicativo ASP.NET Web Forms baseado em declarações usando o WIF</span><span class="sxs-lookup"><span data-stu-id="87a27-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
