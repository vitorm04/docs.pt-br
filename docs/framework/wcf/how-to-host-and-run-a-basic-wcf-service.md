---
title: 'Tutorial: Hospedar e executar um serviço básico do Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197900"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Tutorial: Hospedar e executar um serviço básico do Windows Communication Foundation

Este tutorial descreve o terceiro de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).

A próxima tarefa para a criação de um aplicativo WCF é hospedar um serviço WCF em um aplicativo de console. Um serviço WCF expõe uma ou mais *pontos de extremidade*, cada um deles expõe uma ou mais operações de serviço. Um ponto de extremidade de serviço Especifica as informações a seguir: 
- Um endereço em que você pode encontrar o serviço.
- Uma associação que contém as informações que descrevem como um cliente deve se comunicar com o serviço. 
- Um contrato que define a funcionalidade que o serviço fornece a seus clientes.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.
> - Adicione código para hospedar o serviço WCF.
> - Atualize o arquivo de configuração.
> - Inicie o serviço do WCF e verificar se ele está em execução.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Criar e configurar um projeto de aplicativo de console para hospedar o serviço

1. Crie um projeto de aplicativo de console no Visual Studio: 
 
    1. Dos **arquivo** menu, selecione **abra** > **projeto/solução** e navegue até o **GettingStarted** solução você criado anteriormente (*GettingStarted.sln*). Selecione **Abrir**.

    2. Dos **modo de exibição** menu, selecione **Gerenciador de soluções**.
    
    3. No **Gerenciador de soluções** janela, selecione a **GettingStarted** solução (nó superior) e, em seguida, selecione **Add** > **denovoprojeto** no menu de atalho. 

    4. No **adicionar novo projeto** janela, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual C#**  ou **Visual Basic**. 

    5. Selecione o **aplicativo de Console (.NET Framework)** modelo e insira *GettingStartedHost* para o **nome**. Selecione **OK**.

2. Adicionar uma referência na **GettingStartedHost** do projeto para o **GettingStartedLib** projeto: 

    1. No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedHost** do projeto e, em seguida, selecione **Add Reference** no menu de atalho. 

    2. No **adicionar referência** caixa de diálogo, em **projetos** no lado esquerdo da janela, selecione **solução**. 
 
    3. Selecione **GettingStartedLib** na seção central da janela e, em seguida, selecione **Okey**. 

       Essa ação faz com que os tipos definidos na **GettingStartedLib** projeto disponível para o **GettingStartedHost** projeto.

3. Adicionar uma referência na **GettingStartedHost** do projeto para o <xref:System.ServiceModel> assembly: 

    1. No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedHost** do projeto e, em seguida, selecione **Add Reference** no menu de atalho.
    
    2. No **adicionar referência** janela, em **Assemblies** no lado esquerdo da janela, selecione **Framework**. 

    3. Selecione **System. ServiceModel**e, em seguida, selecione **Okey**. 
    
    4. Salve a solução selecionando **arquivo** > **Salvar tudo**.

## <a name="add-code-to-host-the-service"></a>Adicione código para hospedar o serviço

Para hospedar o serviço, é possível adicionar código para fazer as seguintes etapas: 
   1. Crie um URI para o endereço básico.
   2. Crie uma instância da classe para hospedar o serviço.
   3. Crie um ponto de extremidade de serviço.
   4. Ative a troca de metadados.
   5. Abra o host de serviço para escutar as mensagens de entrada.
  
Faça as seguintes alterações no código:

1. Abra o **Program.cs** ou **Module1.vb** de arquivo no **GettingStartedHost** do projeto e substitua seu código com o código a seguir:

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
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
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    Para obter informações sobre como esse código funciona, consulte [serviço de hospedagem de etapas de programa](#service-hosting-program-steps).

2. Atualize as propriedades do projeto:

   1. No **Gerenciador de soluções** janela, selecione a **GettingStartedHost** pasta e, em seguida, selecione **propriedades** no menu de atalho.

   2. Sobre o **GettingStartedHost** página de propriedades, selecione a **aplicativo** guia:

      - Para C# projetos, selecionados **GettingStartedHost.Program** do **objeto de inicialização** lista.

      - Para projetos do Visual Basic, selecione **Service.Program** da **objeto de inicialização** lista.

   3. Dos **arquivo** menu, selecione **Salvar tudo**.

## <a name="verify-the-service-is-working"></a>Verifique se que o serviço está funcionando

1. Compile a solução e, em seguida, execute as **GettingStartedHost** console do aplicativo de dentro do Visual Studio. 

    O serviço deve ser executado com privilégios de administrador. Porque o Visual Studio é aberto com privilégios de administrador, quando você executa **GettingStartedHost** no Visual Studio, o aplicativo é executado com privilégios de administrador também. Como alternativa, você pode abrir um novo prompt de comando como administrador (selecione **mais** > **executar como administrador** no menu de atalho) e execute **GettingStartedHost.exe**  dentro dele.

2. Abra um navegador da web e navegue até a página do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Serviços como este exigem a permissão apropriada para registrar endereços HTTP no computador para escuta. As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Etapas de programa de hospedagem de serviço

As etapas no código que você adicionou ao host de serviço são descritas da seguinte maneira:

- **Etapa 1**: Criar uma instância da `Uri` classe para manter o endereço base do serviço. Uma URL que contém um endereço base tem um URI opcional que identifica um serviço. O endereço básico é formatado da seguinte maneira: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. O endereço base para o serviço da Calculadora usa o transporte HTTP, localhost, porta 8000 e o segmento do URI, GettingStarted.

- **Etapa 2**: Criar uma instância da <xref:System.ServiceModel.ServiceHost> classe, que você pode usar para hospedar o serviço. O construtor aceita dois parâmetros: o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.

- **Etapa 3**: Crie uma instância de <xref:System.ServiceModel.Description.ServiceEndpoint>. Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço. O <xref:System.ServiceModel.Description.ServiceEndpoint> construtor é composto de um endereço, uma associação e o tipo de interface de contrato de serviço. O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço. A associação para este exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna e conecta-se aos pontos de extremidade que estão em conformidade com o WS-* especificações. Para obter mais informações sobre associações WCF, consulte [visão geral de associações do WCF](bindings-overview.md). Você pode acrescentar o endereço para o endereço básico para identificar o ponto de extremidade. O código especifica o endereço como CalculatorService e o endereço totalmente qualificado para o ponto de extremidade como `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > Para o .NET Framework versão 4 e posterior, adicionar um ponto de extremidade de serviço é opcional. Para essas versões, se você não adicionar seu código ou a configuração, o WCF adiciona um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço. Para obter mais informações sobre pontos de extremidade padrão, consulte [especificação de um endereço de ponto de extremidade](specifying-an-endpoint-address.md). Para obter mais informações sobre pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificado](simplified-configuration.md) e [configuração simplificado para os serviços WCF](samples/simplified-configuration-for-wcf-services.md).

- **Etapa 4**: Ative a troca de metadados. Os clientes usam a troca de metadados para gerar proxies para chamar as operações de serviço. Para habilitar a troca de metadados, criar uma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da instância, defina sua <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriedade a ser `true`e adicione o `ServiceMetadataBehavior` do objeto para o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção da <xref:System.ServiceModel.ServiceHost> instância.

- **Etapa 5**: Abra <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada. O aplicativo espera que você pressionar **Enter**. Depois que o aplicativo cria uma instância <xref:System.ServiceModel.ServiceHost>, ele executa um bloco try/catch. Para obter mais informações sobre como capturar com segurança exceções geradas pelo <xref:System.ServiceModel.ServiceHost>, consulte [uso Close e Abort para liberar os recursos de cliente do WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Quando você adiciona uma biblioteca de serviço do WCF, o Visual Studio o hospeda para você se depurá-lo, iniciando um host de serviço. Para evitar conflitos, você pode impedir que o Visual Studio hospeda o WCF service library. 
> 1. Selecione o **GettingStartedLib** project no **Gerenciador de soluções** e escolha **propriedades** no menu de atalho.
> 2. Selecione **opções do WCF** e desmarque **iniciar durante a depuração de outro projeto na mesma solução o Host de serviço de WCF**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.
> - Adicione código para hospedar o serviço WCF.
> - Atualize o arquivo de configuração.
> - Inicie o serviço do WCF e verificar se ele está em execução.

Avance para o próximo tutorial para aprender a criar um cliente WCF.

> [!div class="nextstepaction"]
> [Tutorial: Criar um cliente WCF](how-to-create-a-wcf-client.md)
