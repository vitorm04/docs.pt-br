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
ms.workload: dotnet
ms.openlocfilehash: c69f79d8629acee80a2e59346032e7733ec37dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="574fd-102">Como definir um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="574fd-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="574fd-103">Esta é a primeira das seis tarefas necessárias para criar um aplicativo [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] básico.</span><span class="sxs-lookup"><span data-stu-id="574fd-103">This is the first of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="574fd-104">Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="574fd-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="574fd-105">Ao criar um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], a primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="574fd-105">When creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service, the first task is to define a service contract.</span></span> <span data-ttu-id="574fd-106">O contrato de serviço especifica a quais operações os serviços dão suporte.</span><span class="sxs-lookup"><span data-stu-id="574fd-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="574fd-107">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="574fd-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="574fd-108">Os contratos são criados definindo uma interface C++, C# ou Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="574fd-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="574fd-109">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="574fd-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="574fd-110">Cada interface deve ter <xref:System.ServiceModel.ServiceContractAttribute> aplicado a ela e cada operação deve ter o atributo <xref:System.ServiceModel.OperationContractAttribute> aplicado a ela.</span><span class="sxs-lookup"><span data-stu-id="574fd-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="574fd-111">Se um método em uma interface que tem o atributo <xref:System.ServiceModel.ServiceContractAttribute> não tiver o atributo <xref:System.ServiceModel.OperationContractAttribute>, o método não será exposto pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="574fd-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="574fd-112">O código usado para essa tarefa é fornecido no exemplo após o procedimento.</span><span class="sxs-lookup"><span data-stu-id="574fd-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="574fd-113">Para definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="574fd-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="574fd-114">Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] como administrador clicando com o programa de **iniciar** menu e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="574fd-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="574fd-115">Crie um projeto de biblioteca de serviços WCF clicando o **arquivo** menu e selecionando **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="574fd-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="574fd-116">No **novo projeto** caixa de diálogo, no lado esquerdo da caixa de diálogo expandir **Visual C#** para um projeto c# ou **outras linguagens** e **doVisualBasic** para um projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="574fd-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="574fd-117">O idioma selecionado, selecione **WCF** e uma lista de modelos de projeto será exibida na seção central da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="574fd-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="574fd-118">Selecione **biblioteca de serviços WCF**e o tipo `GettingStartedLib` no **nome** caixa de texto e `GettingStarted` no **nome da solução** caixa de texto na parte inferior da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="574fd-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="574fd-119">O Visual Studio criará o projeto que contém 3 arquivos: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb) e App.config.  O arquivo IService1 contém um contrato de serviço padrão.</span><span class="sxs-lookup"><span data-stu-id="574fd-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="574fd-120">O arquivo Service1 contém uma implementação padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="574fd-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="574fd-121">O arquivo App.config contém a configuração necessária para carregar o serviço padrão com o Host de Serviço WCF do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="574fd-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="574fd-122">Para obter mais informações sobre a ferramenta de Host de serviço do WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="574fd-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="574fd-123">Abra o arquivo IService1.cs ou IService1.vb e exclua o código dentro da declaração de namespace deixando a declaração do namespace.</span><span class="sxs-lookup"><span data-stu-id="574fd-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="574fd-124">Dentro da declaração do namespace, defina uma nova interface chamada `ICalculator` conforme mostrado no código abaixo.</span><span class="sxs-lookup"><span data-stu-id="574fd-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
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
  
     <span data-ttu-id="574fd-125">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="574fd-125">This contract defines an online calculator.</span></span> <span data-ttu-id="574fd-126">Observe que a interface do `ICalculator` está marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="574fd-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="574fd-127">Esse atributo define um namespace que é usado para remover a ambiguidade do nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="574fd-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="574fd-128">Cada operação da calculadora é marcada com o atributo <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="574fd-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="574fd-129">Ao usar atributos para fazer anotações em uma interface, membro ou classe, você poderá soltar a parte "Atributo" do nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="574fd-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="574fd-130">Portanto, <xref:System.ServiceModel.ServiceContractAttribute> se transforma em `[ServiceContract]` no C# ou `<ServiceContract>` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="574fd-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="574fd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="574fd-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="574fd-132">Como implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="574fd-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="574fd-133">Introdução</span><span class="sxs-lookup"><span data-stu-id="574fd-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="574fd-134">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="574fd-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
