---
title: Como habilitar o WIF para um aplicativo de serviço Web WCF
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: c3d22d812fdd5a1fc7567b3da34e7fd5a59531cd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084833"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="d2cf0-102">Como habilitar o WIF para um aplicativo de serviço Web WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="d2cf0-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="d2cf0-103">Applies To</span></span>  
  
-   <span data-ttu-id="d2cf0-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="d2cf0-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="d2cf0-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d2cf0-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>  
  
## <a name="summary"></a><span data-ttu-id="d2cf0-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="d2cf0-106">Summary</span></span>  
 <span data-ttu-id="d2cf0-107">Estas instruções fornecem procedimentos passo a passo detalhados para habilitar o WIF em um serviço Web WCF.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="d2cf0-108">Também fornecem explicações sobre como testar o aplicativo para verificar se o serviço Web está apresentando declarações corretamente quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="d2cf0-109">Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="d2cf0-110">O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="d2cf0-111">Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="d2cf0-112">O download pode ser feito na seguinte localização: [Ferramenta de Identidade e Acesso](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="d2cf0-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="d2cf0-113">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="d2cf0-113">Contents</span></span>  
  
-   <span data-ttu-id="d2cf0-114">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d2cf0-114">Objectives</span></span>  
  
-   <span data-ttu-id="d2cf0-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d2cf0-115">Overview</span></span>  
  
-   <span data-ttu-id="d2cf0-116">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="d2cf0-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d2cf0-117">Etapa 1 – Criar um serviço WCF simples</span><span class="sxs-lookup"><span data-stu-id="d2cf0-117">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="d2cf0-118">Etapa 2 – Criar um aplicativo cliente para o serviço WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-118">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="d2cf0-119">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="d2cf0-119">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="d2cf0-120">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d2cf0-120">Objectives</span></span>  
  
-   <span data-ttu-id="d2cf0-121">Criar um serviço WCF que requer tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d2cf0-121">Create a WCF service that requires issued tokens</span></span>  
  
-   <span data-ttu-id="d2cf0-122">Criar um cliente WCF que solicita um token de um STS e passa-o ao serviço WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d2cf0-123">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d2cf0-123">Overview</span></span>  
 <span data-ttu-id="d2cf0-124">Estas instruções são destinadas a demonstrar como um desenvolvedor pode usar a autenticação federada ao desenvolver serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="d2cf0-125">Alguns dos benefícios de usar a federação nos serviços WCF incluem:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-125">Some of the benefits of using federation in WCF services include:</span></span>  
  
1.  <span data-ttu-id="d2cf0-126">Fatorar a lógica de autenticação fora do código de serviço WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-126">Factoring authentication logic out of WCF service code</span></span>  
  
2.  <span data-ttu-id="d2cf0-127">Reutilizar soluções existentes do gerenciamento de identidade</span><span class="sxs-lookup"><span data-stu-id="d2cf0-127">Re-using existing identity management solutions</span></span>  
  
3.  <span data-ttu-id="d2cf0-128">Interoperabilidade com outras soluções de identidade</span><span class="sxs-lookup"><span data-stu-id="d2cf0-128">Interoperability with other identity solutions</span></span>  
  
4.  <span data-ttu-id="d2cf0-129">Flexibilidade e superação em alterações futuras</span><span class="sxs-lookup"><span data-stu-id="d2cf0-129">Flexibility and resilience to future changes</span></span>  
  
 <span data-ttu-id="d2cf0-130">O WIF e a Ferramenta de Identidade e Acesso associada tornam mais fácil desenvolver e testar um serviço WCF usando a autenticação federada, conforme demonstrado nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="d2cf0-131">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="d2cf0-131">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d2cf0-132">Etapa 1 – Criar um serviço WCF simples</span><span class="sxs-lookup"><span data-stu-id="d2cf0-132">Step 1 – Create a Simple WCF Service</span></span>  
  
-   <span data-ttu-id="d2cf0-133">Etapa 2 – Criar um aplicativo cliente para o serviço WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-133">Step 2 – Create a Client Application for the WCF Service</span></span>  
  
-   <span data-ttu-id="d2cf0-134">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="d2cf0-134">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="d2cf0-135">Etapa 1 – Criar um serviço WCF simples</span><span class="sxs-lookup"><span data-stu-id="d2cf0-135">Step 1 – Create a Simple WCF Service</span></span>  
 <span data-ttu-id="d2cf0-136">Nesta etapa, você criará um novo serviço WCF que usa o STS de Desenvolvimento incluído na Ferramenta de Identidade e Acesso.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>  
  
#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="d2cf0-137">Para criar um serviço WCF simples</span><span class="sxs-lookup"><span data-stu-id="d2cf0-137">To create a simple WCF service</span></span>  
  
1.  <span data-ttu-id="d2cf0-138">Inicie o Visual Studio em modo elevado como administrador.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-138">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="d2cf0-139">No Visual Studio, clique em **Arquivo**, **Novo** e **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="d2cf0-140">Na janela **Novo Projeto**, clique em **Aplicativo de Serviço WCF**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-140">In the **New Project** window, click **WCF Service Application**.</span></span>  
  
4.  <span data-ttu-id="d2cf0-141">Em **Nome**, insira `TestService` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-141">In **Name**, enter `TestService` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="d2cf0-142">Clique com o botão direito do mouse no projeto **TestService** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="d2cf0-143">A janela **Identidade e Acesso** é exibida.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="d2cf0-144">Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="d2cf0-145">A Ferramenta de Identidade e Acesso configura o serviço para usar o WIF e externalizar a autenticação do STS de Desenvolvimento Local (**LocalSTS**) adicionando elementos de configuração ao arquivo *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>  
  
7.  <span data-ttu-id="d2cf0-146">No arquivo *Service1.svc.cs*, adicione uma diretiva `using` para o namespace **System.Security.Claims** e substitua o código existente pelos dados a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     <span data-ttu-id="d2cf0-147">O método `ComputeResponse` exibe as propriedades de várias declarações emitidas pelo **LocalSTS**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>  
  
8.  <span data-ttu-id="d2cf0-148">No arquivo *IService1.cs*, substitua o código existente pelos dados a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. <span data-ttu-id="d2cf0-149">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-149">Build the project.</span></span>  
  
10. <span data-ttu-id="d2cf0-150">Pressione **Ctrl+F5** para executar o serviço sem iniciar o depurador.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="d2cf0-151">Uma página da Web deve abrir o serviço e você poderá verificar se o **LocalSTS** está em execução examinando a área de notificação (placa do sistema).</span><span class="sxs-lookup"><span data-stu-id="d2cf0-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d2cf0-152">Tanto o **TestService** quanto o **LocalSTS** devem estar em execução quando você adicionar referências de serviço para o aplicativo cliente na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="d2cf0-153">Etapa 2 – Criar um aplicativo cliente para o serviço WCF</span><span class="sxs-lookup"><span data-stu-id="d2cf0-153">Step 2 – Create a Client Application for the WCF Service</span></span>  
 <span data-ttu-id="d2cf0-154">Nesta etapa, você criará um aplicativo de console que usa o STS de Desenvolvimento para fazer a autenticação com o serviço WCF criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>  
  
#### <a name="to-create-a-client-application"></a><span data-ttu-id="d2cf0-155">Para criar um aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="d2cf0-155">To create a client application</span></span>  
  
1.  <span data-ttu-id="d2cf0-156">No Visual Studio, clique com o botão direito do mouse na solução, clique em **Adicionar** e **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="d2cf0-157">Na janela **Adicionar Novo Projeto**, selecione **Aplicativo do Console** da lista de modelos do **Visual C#**, digite `Client` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="d2cf0-158">O novo projeto será criado na pasta da solução.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-158">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="d2cf0-159">Clique com o botão direito do mouse em **Referências**, no projeto **Cliente** e em **Adicionar Referência de Serviço**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>  
  
4.  <span data-ttu-id="d2cf0-160">Na janela **Adicionar Referência de Serviço**, clique na seta suspensa no botão **Descobrir** e clique em **Serviços em Solução**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="d2cf0-161">O **Endereço** será preenchido automaticamente com o serviço WCF criado anteriormente e o **Namespace** será definido como **ServiceReference1**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="d2cf0-162">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-162">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d2cf0-163">Tanto o **TestService** quanto o **LocalSTS** devem estar em execução quando você adicionar referências de serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>  
  
5.  <span data-ttu-id="d2cf0-164">O Visual Studio gerará classes proxy para o serviço WCF, e adicionará todas as informações de referência necessárias.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="d2cf0-165">Também adicionará elementos no arquivo *App.config* para configurar o cliente para obter um token de STS a fim de fazer a autenticação com o serviço.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="d2cf0-166">Quando esse processo for concluído, o arquivo **Program.cs** será aberto.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="d2cf0-167">Adicione uma diretiva `using` para o **System.ServiceModel** e outra para o **Client.ServiceReference1**, substitua o método **Principal** pelo código a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6.  <span data-ttu-id="d2cf0-168">Abra o arquivo *App.config* e adicione o XML a seguir como o primeiro elemento filho sob o elemento `<system.serviceModel>`, depois salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     <span data-ttu-id="d2cf0-169">Isso desabilita a validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-169">This disables certificate validation.</span></span>  
  
7.  <span data-ttu-id="d2cf0-170">Clique com o botão direito do mouse na solução **TestService** e clique em **Definir Projetos de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="d2cf0-171">A página de propriedades **Projeto de Inicialização** é aberta.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="d2cf0-172">Na página de propriedades **Projeto de Inicialização**, selecione **Vários projetos de inicialização**, clique no campo **Ação** para cada projeto e selecione **Iniciar** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="d2cf0-173">Clique em **OK** para salvar as configurações.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-173">Click **OK** to save the settings.</span></span>  
  
8.  <span data-ttu-id="d2cf0-174">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-174">Build the solution.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="d2cf0-175">Etapa 3 – Testar a solução</span><span class="sxs-lookup"><span data-stu-id="d2cf0-175">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="d2cf0-176">Nesta etapa, você testará o aplicativo WCF com o WIF habilitado e verificará se as declarações estão presentes.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="d2cf0-177">Para testar o aplicativo WCF com o WIF habilitado para declarações</span><span class="sxs-lookup"><span data-stu-id="d2cf0-177">To test your WIF-enabled WCF application for claims</span></span>  
  
1.  <span data-ttu-id="d2cf0-178">Pressione **F5** para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="d2cf0-179">Você deve ver uma janela do console e este texto: **Pressione a tecla Enter para invocar o serviço e qualquer outra tecla para sair do aplicativo:**</span><span class="sxs-lookup"><span data-stu-id="d2cf0-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>  
  
2.  <span data-ttu-id="d2cf0-180">Pressione **Enter** e as seguintes informações das declarações deverão aparecer no console:</span><span class="sxs-lookup"><span data-stu-id="d2cf0-180">Press **Enter**, and the following claims information should appear in the console:</span></span>  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d2cf0-181">Tanto o **TestService** quanto o **LocalSTS** devem estar em execução antes de você pressionar **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="d2cf0-182">Uma página da Web deve abrir o serviço e você poderá verificar se o **LocalSTS** está em execução examinando a área de notificação (placa do sistema).</span><span class="sxs-lookup"><span data-stu-id="d2cf0-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>  
  
3.  <span data-ttu-id="d2cf0-183">Se essas declarações aparecerem no console, você terá feito a autenticação com o STS de forma bem-sucedida para exibir declarações de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d2cf0-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
