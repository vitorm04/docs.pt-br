---
title: Como hospedar e executar um serviço básico do Windows Communication Foundation
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e1c00abfec36622f5da493165259fb1786ab8d6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="6993d-102">Como hospedar e executar um serviço básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6993d-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="6993d-103">Esta é a terceira das seis tarefas necessárias para criar um aplicativo [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6993d-103">This is the third of six tasks required to create a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="6993d-104">Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6993d-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="6993d-105">Este tópico descreve como hospedar um serviço do [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6993d-105">This topic describes how to host a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service in a console application.</span></span> <span data-ttu-id="6993d-106">Este procedimento consiste nas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="6993d-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="6993d-107">Crie um projeto de aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="6993d-108">Crie um host de serviço para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="6993d-109">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="6993d-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="6993d-110">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-110">Open the service host.</span></span>  
  
 <span data-ttu-id="6993d-111">Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.</span><span class="sxs-lookup"><span data-stu-id="6993d-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="6993d-112">Para criar um novo aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="6993d-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="6993d-113">Criar um novo projeto de aplicativo de Console clicando na solução Introdução, selecionar, **adicionar**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="6993d-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="6993d-114">No **adicionar novo projeto** caixa de diálogo no lado esquerdo da caixa de diálogo Selecionar **Windows** em **c#** ou **VB**.</span><span class="sxs-lookup"><span data-stu-id="6993d-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="6993d-115">Na seção central da caixa de diálogo Selecionar **aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="6993d-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="6993d-116">Nomeie o projeto como GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="6993d-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="6993d-117">Definir a estrutura de destino do projeto GettingStartedHost .NET Framework 4.5, clique com o botão direito em **GettingStartedHost** no Gerenciador de soluções e selecionando **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6993d-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="6993d-118">Na caixa suspensa rotulada **Framework de destino** selecione **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="6993d-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="6993d-119">Configuração da estrutura de destino para um projeto VB é um pouco diferente, a caixa de diálogo de propriedades de projeto GettingStartedHost, clique o **compilar** guia no lado esquerdo da tela e, em seguida, clique no **avançadas de compilação Opções** botão no canto inferior esquerdo da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6993d-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="6993d-120">Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Framework de destino**.</span><span class="sxs-lookup"><span data-stu-id="6993d-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="6993d-121">Configuração da estrutura de destino causará [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] para recarregar a solução, pressione **Okey** quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="6993d-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="6993d-122">Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost, clique com o botão direito no **referências** pasta sob o projeto GettingStartedHost no Gerenciador de soluções e selecione **adicionar referência** .</span><span class="sxs-lookup"><span data-stu-id="6993d-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="6993d-123">No **adicionar referência** caixa de diálogo, selecione **solução** no lado esquerdo da caixa de diálogo e selecione GettingStartedLib na seção central da caixa de diálogo e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="6993d-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="6993d-124">Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="6993d-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="6993d-125">Adicione uma referência a System. ServiceModel para o projeto GettingStartedHost clicando com o **referência** pasta no projeto no Gerenciador de soluções e selecione GettingStartedHost **adicionar** Referência.</span><span class="sxs-lookup"><span data-stu-id="6993d-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="6993d-126">No **adicionar referência** caixa de diálogo Selecionar **Framework** no lado esquerdo da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6993d-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="6993d-127">Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="6993d-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="6993d-128">Na seção central da caixa de diálogo Selecionar **System. ServiceModel**, clique no **adicionar** botão e, em seguida, clique no **fechar** botão.</span><span class="sxs-lookup"><span data-stu-id="6993d-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="6993d-129">Salve a solução clicando no botão Salvar Tudo abaixo do menu principal.</span><span class="sxs-lookup"><span data-stu-id="6993d-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="6993d-130">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="6993d-130">To host the service</span></span>  
  
-   <span data-ttu-id="6993d-131">Abra o arquivo Program.cs ou Module.vb e insira o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="6993d-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  <span data-ttu-id="6993d-132">Etapa 1 - Cria uma instância da classe URI para manter o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="6993d-133">Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional.</span><span class="sxs-lookup"><span data-stu-id="6993d-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="6993d-134">O endereço base é formatado da seguinte maneira: [de transporte] :// [nome do computador ou domínio] [: opcional # da porta] / [segmento URI opcional] o endereço base para o serviço da Calculadora usa o transporte HTTP, localhost, porta 8000 e o URI do segmento "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="6993d-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="6993d-135">Etapa 2 - Cria uma instância da classe <xref:System.ServiceModel.ServiceHost> para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="6993d-136">O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="6993d-137">Etapa 3 – cria um <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instância.</span><span class="sxs-lookup"><span data-stu-id="6993d-137">Step 3 – Creates a <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span></span> <span data-ttu-id="6993d-138">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="6993d-139">O <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` construtor, portanto, usa o tipo de interface de contrato de serviço, uma associação e um endereço.</span><span class="sxs-lookup"><span data-stu-id="6993d-139">The <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`  constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="6993d-140">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="6993d-141">A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-\*.</span><span class="sxs-lookup"><span data-stu-id="6993d-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="6993d-142">Para obter mais informações sobre as associações do WCF, consulte [visão geral de associações do WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="6993d-143">O endereço é adicionado ao endereço básico para identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6993d-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="6993d-144">O endereço especificado nesse código é "CalculatorService" para o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"` adicionando um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="6993d-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"` Adding a service endpoint is optional when using .NET Framework 4.0 or later.</span></span> <span data-ttu-id="6993d-145">Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-145">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="6993d-146">Para obter mais informações sobre padrão de pontos de extremidade consulte [especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-146">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6993d-147"> pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-147"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="6993d-148">Adicionar um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="6993d-148">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="6993d-149">Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-149">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="6993d-150">Para obter mais informações sobre padrão de pontos de extremidade consulte [especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-150">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6993d-151"> pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-151"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="6993d-152">Etapa 4 – Ativa a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="6993d-152">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="6993d-153">Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="6993d-153">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="6993d-154">Para habilitar a troca de metadados é criar um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da instância, defina-o do <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade `true`e adicionar o comportamento para o <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` coleção do <xref:System.ServiceModel.ServiceHost> instância.</span><span class="sxs-lookup"><span data-stu-id="6993d-154">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="6993d-155">Etapa 5 – Abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="6993d-155">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="6993d-156">Observe que o código aguarda o usuário pressionar ENTER.</span><span class="sxs-lookup"><span data-stu-id="6993d-156">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="6993d-157">Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado.</span><span class="sxs-lookup"><span data-stu-id="6993d-157">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="6993d-158">Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch.</span><span class="sxs-lookup"><span data-stu-id="6993d-158">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="6993d-159">Para obter mais informações sobre segurança Capturando exceções lançadas por <xref:System.ServiceModel.ServiceHost>, consulte [evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6993d-159">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="6993d-160">Para verificar se o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="6993d-160">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="6993d-161">Execute o aplicativo de console GettingStartedHost de dentro do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6993d-161">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="6993d-162">Ao executar em [!INCLUDE[wv](../../../includes/wv-md.md)] e em sistemas operacionais posteriores, o serviço deverá ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="6993d-162">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="6993d-163">Como o [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] foi executado com privilégios de administrador, o GettingStartedHost também será executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="6993d-163">Because [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="6993d-164">Você também pode iniciar um novo prompt de comando executando-o com privilégios de administrador e execute service.exe dentro dele.</span><span class="sxs-lookup"><span data-stu-id="6993d-164">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="6993d-165">Abra o Internet Explorer e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="6993d-165">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6993d-166">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6993d-166">Example</span></span>  
 <span data-ttu-id="6993d-167">O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6993d-167">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="6993d-168">Para compilar isso com um compilador de linha de comando, compilar Iservice1 e Service1 em uma biblioteca de classe referência `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="6993d-168">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="6993d-169">E compile Program.cs em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6993d-169">And compile Program.cs to a console application.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
```  
  
```vb
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="6993d-170">Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta.</span><span class="sxs-lookup"><span data-stu-id="6993d-170">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="6993d-171">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="6993d-171">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6993d-172"> como definir reservas de namespace, consulte [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-172"> how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="6993d-173">Ao executar em [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], o arquivo service.exe deverá ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="6993d-173">When running under [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="6993d-174">Agora o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="6993d-174">Now the service is running.</span></span> <span data-ttu-id="6993d-175">Vá para [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-175">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="6993d-176">Para obter informações de solução de problemas, consulte [o Tutorial de introdução de solução de problemas](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6993d-176">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6993d-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6993d-177">See Also</span></span>  
 [<span data-ttu-id="6993d-178">Introdução</span><span class="sxs-lookup"><span data-stu-id="6993d-178">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="6993d-179">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="6993d-179">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
