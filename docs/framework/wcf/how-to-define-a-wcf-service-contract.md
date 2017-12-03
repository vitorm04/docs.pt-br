---
title: "Como definir um contrato de serviço do Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 062167742a70307949624066b8607a37d5c7ed71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Como definir um contrato de serviço do Windows Communication Foundation
Esta é a primeira das seis tarefas necessárias para criar um aplicativo [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] básico. Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.  
  
 Ao criar um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], a primeira tarefa é definir um contrato de serviço. O contrato de serviço especifica a quais operações os serviços dão suporte. Uma operação pode ser considerada como um método de serviço Web. Os contratos são criados definindo uma interface C++, C# ou Visual Basic (VB). Cada método na interface corresponde a uma operação de serviço específica. Cada interface deve ter <xref:System.ServiceModel.ServiceContractAttribute> aplicado a ela e cada operação deve ter o atributo <xref:System.ServiceModel.OperationContractAttribute> aplicado a ela. Se um método em uma interface que tem o atributo <xref:System.ServiceModel.ServiceContractAttribute> não tiver o atributo <xref:System.ServiceModel.OperationContractAttribute>, o método não será exposto pelo serviço.  
  
 O código usado para essa tarefa é fornecido no exemplo após o procedimento.  
  
### <a name="to-define-a-service-contract"></a>Para definir um contrato de serviço  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] como administrador clicando com o programa de **iniciar** menu e selecionando **executar como administrador**.  
  
2.  Crie um projeto de biblioteca de serviços WCF clicando o **arquivo** menu e selecionando **novo**, **projeto**. No **novo projeto** caixa de diálogo, no lado esquerdo da caixa de diálogo expandir **Visual C#** para um projeto c# ou **outras linguagens** e **doVisualBasic** para um projeto do Visual Basic. O idioma selecionado, selecione **WCF** e uma lista de modelos de projeto será exibida na seção central da caixa de diálogo. Selecione **biblioteca de serviços WCF**e o tipo `GettingStartedLib` no **nome** caixa de texto e `GettingStarted` no **nome da solução** caixa de texto na parte inferior da caixa de diálogo.  
  
3.  O Visual Studio criará o projeto que contém 3 arquivos: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb) e App.config.  O arquivo IService1 contém um contrato de serviço padrão.  O arquivo Service1 contém uma implementação padrão do contrato de serviço. O arquivo App.config contém a configuração necessária para carregar o serviço padrão com o Host de Serviço WCF do Visual Studio. Para obter mais informações sobre a ferramenta de Host de serviço do WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  Abra o arquivo IService1.cs ou IService1.vb e exclua o código dentro da declaração de namespace deixando a declaração do namespace. Dentro da declaração do namespace, defina uma nova interface chamada `ICalculator` conforme mostrado no código abaixo.  
  
    ```  
    // IService.cs  
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
  
    ```  
    ‘IService.vb  
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
  
     Este contrato define uma calculadora online. Observe que a interface do `ICalculator` está marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>. Esse atributo define um namespace que é usado para remover a ambiguidade do nome do contrato. Cada operação da calculadora é marcada com o atributo <xref:System.ServiceModel.OperationContractAttribute>.  
  
    > [!NOTE]
    >  Ao usar atributos para fazer anotações em uma interface, membro ou classe, você poderá soltar a parte "Atributo" do nome do atributo. Portanto, <xref:System.ServiceModel.ServiceContractAttribute> se transforma em `[ServiceContract]` no C# ou `<ServiceContract>` no Visual Basic.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md) (Como implementar um contrato de serviço)  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Hospedagem interna](../../../docs/framework/wcf/samples/self-host.md)
