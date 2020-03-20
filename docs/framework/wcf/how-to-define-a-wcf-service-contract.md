---
title: 'Tutorial: Defina um contrato de serviço da Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184087"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Tutorial: Defina um contrato de serviço da Windows Communication Foundation

Este tutorial descreve a primeira das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).

Quando você cria um serviço WCF, sua primeira tarefa é definir um contrato de serviço. O contrato de serviço especifica a quais operações o serviço dá suporte. Uma operação pode ser considerada como um método de serviço Web. Você cria contratos de serviço definindo uma interface C# ou Visual Basic. Uma interface tem as seguintes características:

- Cada método na interface corresponde a uma operação de serviço específica.
- Para cada interface, você <xref:System.ServiceModel.ServiceContractAttribute> deve aplicar o atributo.
- Para cada operação/método, você <xref:System.ServiceModel.OperationContractAttribute> deve aplicar o atributo.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie um projeto **de Biblioteca de Serviços WCF.**
> - Defina uma interface de contrato de serviço.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Crie um projeto de Biblioteca de Serviços WCF e defina uma interface de contrato de serviço

1. Abra o Visual Studio como administrador. Para isso, selecione o programa Visual Studio no menu **Iniciar** e selecione **Mais** > **Executar como administrador** no menu de atalho.

2. Crie um projeto **de Biblioteca de Serviços WCF.**

   1. No menu **Arquivo**, selecione **Novo** > **Projeto**.

   2. Na caixa de diálogo **Novo Projeto,** no lado esquerdo, expanda **visual C#** ou **Visual Basic**e selecione a categoria **WCF.** O Visual Studio exibe uma lista de modelos de projeto na seção central da janela. Selecione **biblioteca de serviços WCF**.

      > [!NOTE]
      > Se você não ver a categoria de modelo de projeto **WCF,** talvez seja necessário instalar o componente da **Windows Communication Foundation** do Visual Studio. Na caixa de diálogo **Novo Projeto,** selecione o link **Instalador do Estúdio Visual Aberto** no lado esquerdo. Selecione a guia **Componentes Individuais** e, em seguida, encontre e selecione **a Fundação de Comunicação do Windows** na categoria **Atividades de Desenvolvimento.** Escolha **Modificar** para começar a instalar o componente.

   3. Na seção inferior da janela, *digite GettingStartedLib* para o **nome** e *GettingStarted* para o **nome da solução**.

   4. Selecione **OK**.

      O Visual Studio cria o projeto, que possui três arquivos: *IService1.cs* (ou *IService1.vb* para um projeto Visual Basic), *Service1.cs* (ou *Service1.vb* para um projeto Visual Basic) e *App.config*. O Visual Studio define esses arquivos da seguinte forma:
      - O arquivo *IService1* contém a definição padrão do contrato de serviço.
      - O arquivo *Service1* contém a implementação padrão do contrato de serviço.
      - O arquivo *App.config* contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta Visual Studio WCF Service Host. Para obter mais informações sobre a ferramenta Host de serviço wcf, consulte [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Se você instalou o Visual Studio com as configurações do ambiente de desenvolvedor Visual Basic, a solução pode estar oculta. Se esse for o caso, selecione **Opções** no menu **Ferramentas** e selecione **Projetos e Soluções** > **Gerais** na janela **Opções.** Selecione **Sempre mostrar solução**. Além disso, verifique **se salvar novos projetos quando criado sao** selecionados.

3. A partir **do Solution Explorer,** abra o arquivo **IService1.cs** ou **IService1.vb** e substitua seu código pelo seguinte código:

    ```csharp
    using System;
    using System.ServiceModel;

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

    ```vb
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

     Este contrato define uma calculadora online. Observe `ICalculator` que a interface <xref:System.ServiceModel.ServiceContractAttribute> está marcada `ServiceContract`com o atributo (simplificado como ). Este atributo define um namespace para desambiguar o nome do contrato. O código marca cada operação <xref:System.ServiceModel.OperationContractAttribute> da calculadora `OperationContract`com o atributo (simplificado como ).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Crie um projeto de Biblioteca de Serviços WCF.
> - Defina uma interface de contrato de serviço.

Avance para o próximo tutorial para saber como implementar o contrato de serviço wcf.

> [!div class="nextstepaction"]
> [Tutorial: Implementar um contrato de serviço WCF](how-to-implement-a-wcf-contract.md)
