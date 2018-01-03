---
title: "Como habilitar o WIF para um aplicativo de serviço Web WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1af6fc1b7802fe69f0585011322e2485695a030c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Como habilitar o WIF para um aplicativo de serviço Web WCF
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>Resumo  
 Estas instruções fornecem procedimentos passo a passo detalhados para habilitar o WIF em um serviço Web WCF. Também fornecem explicações sobre como testar o aplicativo para verificar se o serviço Web está apresentando declarações corretamente quando o aplicativo é executado. Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso. O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes. Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções. O download pode ser feito na seguinte localização: [Ferramenta de Identidade e Acesso](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Visão geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – Criar um serviço WCF simples  
  
-   Etapa 2 – Criar um aplicativo cliente para o serviço WCF  
  
-   Etapa 3 – Testar a solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Criar um serviço WCF que requer tokens emitidos  
  
-   Criar um cliente WCF que solicita um token de um STS e passa-o ao serviço WCF  
  
## <a name="overview"></a>Visão geral  
 Estas instruções são destinadas a demonstrar como um desenvolvedor pode usar a autenticação federada ao desenvolver serviços WCF. Alguns dos benefícios de usar a federação nos serviços WCF incluem:  
  
1.  Fatorar a lógica de autenticação fora do código de serviço WCF  
  
2.  Reutilizar soluções existentes do gerenciamento de identidade  
  
3.  Interoperabilidade com outras soluções de identidade  
  
4.  Flexibilidade e superação em alterações futuras  
  
 O WIF e a Ferramenta de Identidade e Acesso associada tornam mais fácil desenvolver e testar um serviço WCF usando a autenticação federada, conforme demonstrado nas etapas a seguir.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – Criar um serviço WCF simples  
  
-   Etapa 2 – Criar um aplicativo cliente para o serviço WCF  
  
-   Etapa 3 – Testar a solução  
  
## <a name="step-1--create-a-simple-wcf-service"></a>Etapa 1 – Criar um serviço WCF simples  
 Nesta etapa, você criará um novo serviço WCF que usa o STS de Desenvolvimento incluído na Ferramenta de Identidade e Acesso.  
  
#### <a name="to-create-a-simple-wcf-service"></a>Para criar um serviço WCF simples  
  
1.  Inicie o Visual Studio em modo elevado como administrador.  
  
2.  No Visual Studio, clique em **Arquivo**, **Novo** e **Projeto**.  
  
3.  Na janela **Novo Projeto**, clique em **Aplicativo de Serviço WCF**.  
  
4.  Em **Nome**, insira `TestService` e pressione **OK**.  
  
5.  Clique com o botão direito do mouse no projeto **TestService** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.  
  
6.  A janela **Identidade e Acesso** é exibida. Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**. A Ferramenta de Identidade e Acesso configura o serviço para usar o WIF e externalizar a autenticação do STS de Desenvolvimento Local (**LocalSTS**) adicionando elementos de configuração ao arquivo *Web.config*.  
  
7.  No arquivo *Service1.svc.cs*, adicione uma diretiva `using` para o namespace **System.Security.Claims** e substitua o código existente pelos dados a seguir e salve o arquivo:  
  
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
  
     O método `ComputeResponse` exibe as propriedades de várias declarações emitidas pelo **LocalSTS**.  
  
8.  No arquivo *IService1.cs*, substitua o código existente pelos dados a seguir e salve o arquivo:  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. Compile o projeto.  
  
10. Pressione **Ctrl+F5** para executar o serviço sem iniciar o depurador. Uma página da Web deve abrir o serviço e você poderá verificar se o **LocalSTS** está em execução examinando a área de notificação (placa do sistema).  
  
    > [!IMPORTANT]
    >  Tanto o **TestService** quanto o **LocalSTS** devem estar em execução quando você adicionar referências de serviço para o aplicativo cliente na próxima etapa.  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Etapa 2 – Criar um aplicativo cliente para o serviço WCF  
 Nesta etapa, você criará um aplicativo de console que usa o STS de Desenvolvimento para fazer a autenticação com o serviço WCF criado na etapa anterior.  
  
#### <a name="to-create-a-client-application"></a>Para criar um aplicativo cliente  
  
1.  No Visual Studio, clique com o botão direito do mouse na solução, clique em **Adicionar** e **Novo Projeto**.  
  
2.  Na janela **Adicionar Novo Projeto**, selecione **Aplicativo do Console** da lista de modelos do **Visual C#**, digite `Client` e pressione **OK**. O novo projeto será criado na pasta da solução.  
  
3.  Clique com o botão direito do mouse em **Referências**, no projeto **Cliente** e em **Adicionar Referência de Serviço**.  
  
4.  Na janela **Adicionar Referência de Serviço**, clique na seta suspensa no botão **Descobrir** e clique em **Serviços em Solução**. O **Endereço** será preenchido automaticamente com o serviço WCF criado anteriormente e o **Namespace** será definido como **ServiceReference1**. Clique em **OK**.  
  
    > [!IMPORTANT]
    >  Tanto o **TestService** quanto o **LocalSTS** devem estar em execução quando você adicionar referências de serviço para o cliente.  
  
5.  O Visual Studio gerará classes proxy para o serviço WCF, e adicionará todas as informações de referência necessárias. Também adicionará elementos no arquivo *App.config* para configurar o cliente para obter um token de STS a fim de fazer a autenticação com o serviço. Quando esse processo for concluído, o arquivo **Program.cs** será aberto. Adicione uma diretiva `using` para o **System.ServiceModel** e outra para o **Client.ServiceReference1**, substitua o método **Principal** pelo código a seguir e salve o arquivo:  
  
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
  
6.  Abra o arquivo *App.config* e adicione o XML a seguir como o primeiro elemento filho sob o elemento `<system.serviceModel>`, depois salve o arquivo:  
  
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
  
     Isso desabilita a validação de certificado.  
  
7.  Clique com o botão direito do mouse na solução **TestService** e clique em **Definir Projetos de Inicialização**. A página de propriedades **Projeto de Inicialização** é aberta. Na página de propriedades **Projeto de Inicialização**, selecione **Vários projetos de inicialização**, clique no campo **Ação** para cada projeto e selecione **Iniciar** no menu suspenso. Clique em **OK** para salvar as configurações.  
  
8.  Compile a solução.  
  
## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução  
 Nesta etapa, você testará o aplicativo WCF com o WIF habilitado e verificará se as declarações estão presentes.  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Para testar o aplicativo WCF com o WIF habilitado para declarações  
  
1.  Pressione **F5** para compilar e executar o aplicativo. Você deve ver uma janela do console e este texto: **Pressione a tecla Enter para invocar o serviço e qualquer outra tecla para sair do aplicativo:**  
  
2.  Pressione **Enter** e as seguintes informações das declarações deverão aparecer no console:  
  
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
    >  Tanto o **TestService** quanto o **LocalSTS** devem estar em execução antes de você pressionar **Enter**. Uma página da Web deve abrir o serviço e você poderá verificar se o **LocalSTS** está em execução examinando a área de notificação (placa do sistema).  
  
3.  Se essas declarações aparecerem no console, você terá feito a autenticação com o STS de forma bem-sucedida para exibir declarações de serviço WCF.
