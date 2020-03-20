---
title: 'Tutorial: Hospede e execute um serviço básico da Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184079"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Tutorial: Hospede e execute um serviço básico da Windows Communication Foundation

Este tutorial descreve a terceira das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).

A próxima tarefa para criar um aplicativo WCF é hospedar um serviço WCF em um aplicativo de console. Um serviço WCF expõe um ou mais *pontos finais*, cada um dos quais expõe uma ou mais operações de serviço. Um ponto final de serviço especifica as seguintes informações:

- Um endereço onde você pode encontrar o serviço.
- Uma vinculação que contém as informações que descrevem como um cliente deve se comunicar com o serviço.
- Um contrato que define a funcionalidade que o serviço oferece aos seus clientes.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie e configure um projeto de aplicativo de console para hospedar um serviço WCF.
> - Adicione código para hospedar o serviço WCF.
> - Atualize o arquivo de configuração.
> - Inicie o serviço WCF e verifique se está em execução.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Crie e configure um projeto de aplicativo de console para hospedar o serviço

1. Crie um projeto de aplicativo de console no Visual Studio:

    1. No menu **Arquivo,** selecione **Abrir** > **projeto/solução** e navegue até a solução **GettingStarted** criada anteriormente *(GettingStarted.sln*). Selecione **Abrir**.

    2. No menu **Exibir,** selecione **Solution Explorer**.

    3. Na janela **Solution Explorer,** selecione a solução **GettingStarted** (nó superior e selecione **Adicionar** > **novo projeto** no menu de atalho.

    4. Na janela **Adicionar novo projeto,** no lado esquerdo, selecione a categoria **Windows Desktop** em **Visual C#** ou **Visual Basic**.

    5. Selecione o modelo **Console App (.NET Framework)** e insira *GettingStartedHost* para o **Nome**. Selecione **OK**.

2. Adicione uma referência no projeto **GettingStartedHost** ao projeto **GettingStartedLib:**

    1. Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedHost** e selecione **Adicionar referência** no menu de atalho.

    2. Na caixa de diálogo **Adicionar referência,** em **Projetos** no lado esquerdo da janela, selecione **Solução**.

    3. Selecione **GettingStartedLib** na seção central da janela e, em seguida, selecione **OK**.

       Essa ação torna os tipos definidos no projeto **GettingStartedLib** disponíveis para o projeto **GettingStartedHost.**

3. Adicione uma referência no projeto **GettingStartedHost** à <xref:System.ServiceModel> montagem:

    1. Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedHost** e selecione **Adicionar referência** no menu de atalho.

    2. Na janela **Adicionar referência,** em **Montagens** no lado esquerdo da janela, **selecione Quadro**.

    3. Selecione **System.ServiceModel**e selecione **OK**.

    4. Salve a solução selecionando **'Salvar todos'** **do arquivo** > .

## <a name="add-code-to-host-the-service"></a>Adicionar código para hospedar o serviço

Para hospedar o serviço, adicione código para fazer as seguintes etapas:

1. Crie um URI para o endereço base.
2. Crie uma instância de classe para hospedar o serviço.
3. Crie um ponto final de serviço.
4. Ative a troca de metadados.
5. Abra o host de serviço para ouvir as mensagens recebidas.
  
Faça as alterações a seguir ao código:

1. Abra o arquivo **Program.cs** ou **Module1.vb** no projeto **GettingStartedHost** e substitua seu código pelo seguinte código:

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

    Para obter informações sobre como esse código funciona, consulte [as etapas do programa de hospedagem de serviços](#service-hosting-program-steps).

2. Atualize as propriedades do projeto:

   1. Na janela **'Explorador de soluções',** selecione a pasta **GettingStartedHost** e selecione **Propriedades** no menu de atalho.

   2. Na página **Propriedades GettingStartedHost,** selecione a guia **Aplicativo:**

      - Para projetos C#, selecione **GettingStartedHost.Program** na lista **de objetos Iniciar.**

      - Para projetos Visual Basic, selecione **Service.Program** na lista **de objetos Iniciar.**

   3. No menu **Arquivo,** selecione **Salvar tudo**.

## <a name="verify-the-service-is-working"></a>Verifique se o serviço está funcionando

1. Crie a solução e execute o aplicativo de console **GettingStartedHost** de dentro do Visual Studio.

    O serviço deve ser executado com privilégios de administrador. Como você abriu o Visual Studio com privilégios de administrador, quando executa **o GettingStartedHost** no Visual Studio, o aplicativo também é executado com privilégios de administrador. Como alternativa, você pode abrir um novo prompt de comando como administrador (selecione **Mais** > **Executar como administrador** no menu de atalho) e executar **GettingStartedHost.exe** dentro dele.

2. Abra um navegador da Web e navegue até a página do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.

   > [!NOTE]
   > Serviços como este exigem a permissão adequada para registrar endereços HTTP na máquina para ouvir. As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](feature-details/configuring-http-and-https.md).

## <a name="service-hosting-program-steps"></a>Etapas do programa de hospedagem de serviços

As etapas do código adicionado para hospedar o serviço são descritas da seguinte forma:

- **Passo 1**: Crie `Uri` uma instância da classe para manter o endereço base do serviço. Uma URL que contém um endereço base tem um URI opcional que identifica um serviço. O endereço base é formatado `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`da seguinte forma: . O endereço base do serviço de calculadora usa o transporte HTTP, localhost, port 8000 e o segmento URI, GettingStarted.

- **Passo 2**: Crie <xref:System.ServiceModel.ServiceHost> uma instância da classe, que você usa para hospedar o serviço. A construtora tem dois parâmetros: o tipo da classe que implementa o contrato de serviço e o endereço base do serviço.

- **Passo 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Criar uma instância. Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço. O <xref:System.ServiceModel.Description.ServiceEndpoint> construtor é composto pelo tipo de interface de contrato de serviço, uma vinculação e um endereço. O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço. A vinculação para <xref:System.ServiceModel.WSHttpBinding>esta amostra é , que é uma ligação incorporada e se conecta a pontos finais que estão de acordo com as especificações WS-*. Para obter mais informações sobre as vinculações do WCF, consulte [a visão geral das vinculações do WCF](bindings-overview.md). Você anexa o endereço ao endereço base para identificar o ponto final. O código especifica o endereço como CalculatorService e o `http://localhost:8000/GettingStarted/CalculatorService`endereço totalmente qualificado para o ponto final como .

    > [!IMPORTANT]
    > Para .NET Framework Version 4 e posterior, adicionar um ponto final de serviço é opcional. Para essas versões, se você não adicionar seu código ou configuração, o WCF adicionará um ponto final padrão para cada combinação de endereço base e contrato implementado pelo serviço. Para obter mais informações sobre pontos finais padrão, consulte [Especificando um endereço de ponto final](specifying-an-endpoint-address.md). Para obter mais informações sobre pontos finais padrão, vinculações e comportamentos, consulte [Configuração simplificada](simplified-configuration.md) e [configuração simplificada para serviços WCF](samples/simplified-configuration-for-wcf-services.md).

- **Passo 4**: Habilite a troca de metadados. Os clientes usam a troca de metadados para gerar proxies para chamar as operações de serviço. Para habilitar a troca <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de metadados, `true`crie uma `ServiceMetadataBehavior` instância, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> defina <xref:System.ServiceModel.ServiceHost> sua <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriedade e adicione o objeto à coleção da instância.

- **Passo 5** <xref:System.ServiceModel.ServiceHost> : Aberto para ouvir as mensagens recebidas. O aplicativo espera que você pressione **Enter**. Depois que o <xref:System.ServiceModel.ServiceHost>aplicativo instancia, ele executa um bloco de tentativa/captura. Para obter mais informações sobre a <xref:System.ServiceModel.ServiceHost>captura segura de exceções lançadas, consulte [Use Close e Abort para liberar recursos do cliente WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Quando você adiciona uma biblioteca de serviços WCF, o Visual Studio a hospeda para você se você depurar, iniciando um host de serviço. Para evitar conflitos, você pode impedir o Visual Studio de hospedar a biblioteca de serviços do WCF.
>
> 1. Selecione o projeto **GettingStartedLib** no **Solution Explorer** e escolha **Propriedades** no menu de atalho.
> 2. Selecione **opções WCF** e desmarque **Iniciar o Host de serviço WCF ao depurar outro projeto na mesma solução**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Crie e configure um projeto de aplicativo de console para hospedar um serviço WCF.
> - Adicione código para hospedar o serviço WCF.
> - Atualize o arquivo de configuração.
> - Inicie o serviço WCF e verifique se está em execução.

Avance para o próximo tutorial para aprender como criar um cliente WCF.

> [!div class="nextstepaction"]
> [Tutorial: Crie um cliente WCF](how-to-create-a-wcf-client.md)
