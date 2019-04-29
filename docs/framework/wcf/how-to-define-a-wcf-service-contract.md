---
title: 'Tutorial: Definir um contrato de serviço do Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929344"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Tutorial: Definir um contrato de serviço do Windows Communication Foundation

Este tutorial descreve o primeiro de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).

Quando você cria um serviço WCF, a primeira tarefa é definir um contrato de serviço. O contrato de serviço especifica a quais operações os serviços dão suporte. Uma operação pode ser considerada como um método de serviço Web. Criar contratos de serviço com a definição de um Visual C# ou a interface do Visual Basic (VB). Uma interface tem as seguintes características:

- Cada método na interface corresponde a uma operação de serviço específica. 
- Para cada interface, você deve aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo.
- Para cada operação/método, você deve aplicar o <xref:System.ServiceModel.OperationContractAttribute> atributo. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Criar uma **WCF Service Library** projeto.
> - Defina uma interface de contrato de serviço.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Criar um projeto de biblioteca de serviço do WCF e definir uma interface de contrato de serviço

1. Abra o Visual Studio como um administrador. Para fazer isso, selecione o programa Visual Studio na **inicie** menu e, em seguida, selecione **mais** > **executar como administrador** no menu de atalho.

2. Criar uma **WCF Service Library** projeto.

   1. No menu **Arquivo**, selecione **Novo** > **Projeto**.

   2. No **novo projeto** caixa de diálogo, no lado esquerdo, expanda **Visual c#** ou **Visual Basic**e, em seguida, selecione o **WCF** categoria. Visual Studio exibe uma lista de modelos de projeto na seção central da janela. Selecione **WCF Service Library**.

      > [!NOTE]
      > Se você não vir as **WCF** categoria do modelo de projeto, você talvez precise instalar o **Windows Communication Foundation** componente do Visual Studio. No **novo projeto** caixa de diálogo, selecione o **abrir instalador do Visual Studio** link no lado esquerdo. Selecione o **componentes individuais** guia e, em seguida, localize e selecione **Windows Communication Foundation** sob o **atividades de desenvolvimento** categoria. Escolher **modificar** para começar a instalação do componente.

   3. Na seção inferior da janela, digite *GettingStartedLib* para o **nome** e *GettingStarted* para o **nome da solução**. 

   4. Selecione **OK**.

      O Visual Studio cria o projeto, que tem três arquivos: *IService1.cs* (ou *IService1.vb* para um projeto do Visual Basic), *Service1.cs* (ou *Service1.vb* para um projeto do Visual Basic), e  *App. config*. O Visual Studio define esses arquivos da seguinte maneira: 
      - O *IService1* arquivo contém a definição padrão do contrato de serviço. 
      - O *Service1* arquivo contém a implementação padrão de contrato de serviço. 
      - O *App. config* arquivo contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta de Host do serviço de WCF do Visual Studio. Para obter mais informações sobre a ferramenta de Host de serviço WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Se você instalou o Visual Studio com as configurações de ambiente de desenvolvedor de Visual Basic, a solução pode estar oculto. Se esse for o caso, selecione **opções** da **ferramentas** menu, em seguida, selecione **projetos e soluções** > **geral** em o **opções** janela. Selecione **sempre mostrar solução**. Além disso, verifique **salvar novos projetos quando criados** está selecionado.

3. Partir **Gerenciador de soluções**, abra o **IService1.cs** ou **IService1.vb** de arquivo e substitua seu código com o código a seguir:

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

     Este contrato define uma calculadora online. Observe que o `ICalculator` interface é marcado com o <xref:System.ServiceModel.ServiceContractAttribute> atributo (simplificada como `ServiceContract`). Este atributo define um namespace para desambiguar o nome do contrato. O código marca cada operação da Calculadora com o <xref:System.ServiceModel.OperationContractAttribute> atributo (simplificada como `OperationContract`).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Crie um projeto de biblioteca de serviço WCF.
> - Defina uma interface de contrato de serviço.

Avance para o próximo tutorial para aprender a implementar o contrato de serviço do WCF.

> [!div class="nextstepaction"]
> [Tutorial: Implementar um contrato de serviço do WCF](how-to-implement-a-wcf-contract.md)
