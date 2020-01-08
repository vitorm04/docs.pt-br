---
title: 'Tutorial: definir um contrato de serviço de Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 49526808a65b68c6df734bd7f3e76eff1e4a6bc5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338291"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Tutorial: definir um contrato de serviço de Windows Communication Foundation

Este tutorial descreve a primeira de cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF). Para obter uma visão geral dos tutoriais, consulte [tutorial: introdução aos aplicativos Windows Communication Foundation](getting-started-tutorial.md).

Quando você cria um serviço WCF, sua primeira tarefa é definir um contrato de serviço. O contrato de serviço especifica a quais operações os serviços dão suporte. Uma operação pode ser considerada como um método de serviço Web. Você cria contratos de serviço definindo uma C# interface ou Visual Basic. Uma interface tem as seguintes características:

- Cada método na interface corresponde a uma operação de serviço específica. 
- Para cada interface, você deve aplicar o atributo <xref:System.ServiceModel.ServiceContractAttribute>.
- Para cada operação/método, você deve aplicar o atributo <xref:System.ServiceModel.OperationContractAttribute>. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie um projeto de **biblioteca de serviços WCF** .
> - Defina uma interface de contrato de serviço.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Criar um projeto de biblioteca de serviço WCF e definir uma interface de contrato de serviço

1. Abra o Visual Studio como um administrador. Para fazer isso, selecione o programa Visual Studio no menu **Iniciar** e, em seguida, selecione **mais** > **Executar como administrador** no menu de atalho.

2. Crie um projeto de **biblioteca de serviços WCF** .

   1. No menu **Arquivo**, selecione **Novo** > **Projeto**.

   2. Na caixa de diálogo **novo projeto** , no lado esquerdo, expanda  **C# Visual** ou **Visual Basic**e, em seguida, selecione a categoria **WCF** . O Visual Studio exibe uma lista de modelos de projeto na seção central da janela. Selecione **biblioteca de serviços WCF**.

      > [!NOTE]
      > Se você não vir a categoria de modelo de projeto do **WCF** , talvez seja necessário instalar o componente **Windows Communication Foundation** do Visual Studio. Na caixa de diálogo **novo projeto** , selecione o link **abrir instalador do Visual Studio** no lado esquerdo. Selecione a guia **componentes individuais** e, em seguida, localize e selecione **Windows Communication Foundation** na categoria **atividades de desenvolvimento** . Escolha **Modificar** para começar a instalar o componente.

   3. Na seção inferior da janela, digite *GettingStartedLib* para o **nome** e *gettingstarted* para o nome da **solução**. 

   4. Selecione **OK**.

      O Visual Studio cria o projeto, que tem três arquivos *: IService1.cs* (ou *IService1. vb* para um projeto Visual Basic), *Service1.cs* (ou *Service1. vb* para um projeto Visual Basic) e *app. config*. O Visual Studio define esses arquivos da seguinte maneira: 
      - O arquivo *IService1* contém a definição padrão do contrato de serviço. 
      - O arquivo *Service1* contém a implementação padrão do contrato de serviço. 
      - O arquivo *app. config* contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta de host do serviço WCF do Visual Studio. Para obter mais informações sobre a ferramenta host de serviço do WCF, consulte [host de serviço WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Se você instalou o Visual Studio com Visual Basic configurações de ambiente de desenvolvedor, a solução pode estar oculta. Se esse for o caso, selecione **Opções** no menu **ferramentas** e, em seguida, selecione **projetos e soluções** > **geral** na janela **Opções** . Selecione **sempre mostrar solução**. Além disso, verifique se **salvar novos projetos quando criado** está selecionado.

3. Em **Gerenciador de soluções**, abra o arquivo **IService1.cs** ou **IService1. vb** e substitua seu código pelo código a seguir:

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

     Este contrato define uma calculadora online. Observe que a interface `ICalculator` está marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute> (simplificado como `ServiceContract`). Esse atributo define um namespace para desambiguar o nome do contrato. O código marca cada operação de calculadora com o atributo <xref:System.ServiceModel.OperationContractAttribute> (simplificado como `OperationContract`).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
>
> - Crie um projeto de biblioteca de serviços WCF.
> - Defina uma interface de contrato de serviço.

Avance para o próximo tutorial para aprender a implementar o contrato de serviço do WCF.

> [!div class="nextstepaction"]
> [Tutorial: implementar um contrato de serviço WCF](how-to-implement-a-wcf-contract.md)
