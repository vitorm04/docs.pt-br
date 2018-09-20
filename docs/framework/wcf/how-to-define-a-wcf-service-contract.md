---
title: Como definir um contrato de serviço do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489153"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Como definir um contrato de serviço do Windows Communication Foundation

Este é o primeiro de seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

 Ao criar um serviço WCF, a primeira tarefa é definir um contrato de serviço. O contrato de serviço especifica a quais operações os serviços dão suporte. Uma operação pode ser considerada como um método de serviço Web. Os contratos são criados definindo uma interface C++, C# ou Visual Basic (VB). Cada método na interface corresponde a uma operação de serviço específica. Cada interface deve ter <xref:System.ServiceModel.ServiceContractAttribute> aplicado a ela e cada operação deve ter o atributo <xref:System.ServiceModel.OperationContractAttribute> aplicado a ela. Se um método em uma interface que tem o atributo <xref:System.ServiceModel.ServiceContractAttribute> não tiver o atributo <xref:System.ServiceModel.OperationContractAttribute>, o método não será exposto pelo serviço.

 O código usado para essa tarefa é fornecido no exemplo após o procedimento.

## <a name="define-a-service-contract"></a>Definir um contrato de serviço

1. Abra o Visual Studio como administrador clicando com o programa a **inicie** menu e selecionando **mais** > **executar como administrador**.

2. Crie um projeto de biblioteca de serviço WCF.

   1. No menu **Arquivo**, selecione **Novo** > **Projeto**.

   2. No **novo projeto** caixa de diálogo, no lado esquerdo, expanda **Visual c#** ou **Visual Basic**e, em seguida, selecione o **WCF** categoria. Uma lista de modelos de projeto é exibida na seção central da caixa de diálogo. Selecione **WCF Service Library**.

   3. Insira `GettingStartedLib` no **nome** caixa de texto e `GettingStarted` no **nome da solução** caixa de texto na parte inferior da caixa de diálogo.

   > [!NOTE]
   > Se você não vir as **WCF** categoria do modelo de projeto, você talvez precise instalar o **Windows Communication Foundation** componente do Visual Studio. No **novo projeto** diálogo caixa, clique no link que diz **abrir instalador do Visual Studio**. Selecione o **componentes individuais** guia e, em seguida, localize e selecione **Windows Communication Foundation** sob o **atividades de desenvolvimento** categoria. Escolher **modificar** para começar a instalação do componente.

   O Visual Studio cria o projeto, que contém 3 arquivos: IService1.cs (ou IService1.vb), Service1.cs (or Service1.vb) e App. config. O arquivo IService1 contém um contrato de serviço padrão. O arquivo Service1 contém uma implementação padrão do contrato de serviço. O arquivo App.config contém a configuração necessária para carregar o serviço padrão com o Host de Serviço WCF do Visual Studio. Para obter mais informações sobre a ferramenta de Host de serviço WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

3. Abra o arquivo IService1.cs ou IService1.vb e exclua o código dentro da declaração de namespace, deixando a declaração de namespace. Dentro da declaração do namespace, defina uma nova interface chamada `ICalculator` conforme mostrado no código abaixo.

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

     Este contrato define uma calculadora online. Observe que a interface do `ICalculator` está marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>. Esse atributo define um namespace que é usado para remover a ambiguidade do nome do contrato. Cada operação da calculadora é marcada com o atributo <xref:System.ServiceModel.OperationContractAttribute>.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como: implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Como implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)