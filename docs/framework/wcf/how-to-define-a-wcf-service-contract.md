---
title: Como definir um contrato de serviço do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 9f7f696b1f5be2e96c50938f4627271d891deb32
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582194"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="7da03-102">Como definir um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7da03-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="7da03-103">Este é o primeiro de seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7da03-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7da03-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7da03-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

 <span data-ttu-id="7da03-105">Ao criar um serviço WCF, a primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="7da03-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="7da03-106">O contrato de serviço especifica a quais operações os serviços dão suporte.</span><span class="sxs-lookup"><span data-stu-id="7da03-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="7da03-107">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="7da03-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="7da03-108">Os contratos são criados definindo uma interface C++, C# ou Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="7da03-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="7da03-109">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="7da03-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="7da03-110">Cada interface deve ter <xref:System.ServiceModel.ServiceContractAttribute> aplicado a ela e cada operação deve ter o atributo <xref:System.ServiceModel.OperationContractAttribute> aplicado a ela.</span><span class="sxs-lookup"><span data-stu-id="7da03-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="7da03-111">Se um método em uma interface que tem o atributo <xref:System.ServiceModel.ServiceContractAttribute> não tiver o atributo <xref:System.ServiceModel.OperationContractAttribute>, o método não será exposto pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="7da03-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>

 <span data-ttu-id="7da03-112">O código usado para essa tarefa é fornecido no exemplo após o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7da03-112">The code used for this task is provided in the example following the procedure.</span></span>

## <a name="define-a-service-contract"></a><span data-ttu-id="7da03-113">Definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7da03-113">Define a service contract</span></span>

1. <span data-ttu-id="7da03-114">Abra o Visual Studio como administrador clicando com o programa a **inicie** menu e selecionando **mais** > **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="7da03-114">Open Visual Studio as an administrator by right-clicking the program in the **Start** menu and selecting **More** > **Run as administrator**.</span></span>

2. <span data-ttu-id="7da03-115">Crie um projeto de biblioteca de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="7da03-115">Create a WCF Service Library project.</span></span>

   1. <span data-ttu-id="7da03-116">No menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="7da03-116">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="7da03-117">No **novo projeto** caixa de diálogo, no lado esquerdo, expanda **Visual c#** ou **Visual Basic**e, em seguida, selecione o **WCF** categoria.</span><span class="sxs-lookup"><span data-stu-id="7da03-117">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="7da03-118">Uma lista de modelos de projeto é exibida na seção central da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7da03-118">A list of project templates is displayed in the center section of the dialog.</span></span> <span data-ttu-id="7da03-119">Selecione **WCF Service Library**.</span><span class="sxs-lookup"><span data-stu-id="7da03-119">Select **WCF Service Library**.</span></span>

   3. <span data-ttu-id="7da03-120">Insira `GettingStartedLib` no **nome** caixa de texto e `GettingStarted` no **nome da solução** caixa de texto na parte inferior da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7da03-120">Enter `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7da03-121">Se você não vir as **WCF** categoria do modelo de projeto, você talvez precise instalar o **Windows Communication Foundation** componente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7da03-121">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="7da03-122">No **novo projeto** diálogo caixa, clique no link que diz **abrir instalador do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7da03-122">In the **New Project** dialog box, click the link that says **Open Visual Studio Installer**.</span></span> <span data-ttu-id="7da03-123">Selecione o **componentes individuais** guia e, em seguida, localize e selecione **Windows Communication Foundation** sob o **atividades de desenvolvimento** categoria.</span><span class="sxs-lookup"><span data-stu-id="7da03-123">Select the **Individual Components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="7da03-124">Escolher **modificar** para começar a instalação do componente.</span><span class="sxs-lookup"><span data-stu-id="7da03-124">Choose **Modify** to begin installing the component.</span></span>

   <span data-ttu-id="7da03-125">O Visual Studio cria o projeto, que contém 3 arquivos: IService1.cs (ou IService1.vb), Service1.cs (or Service1.vb) e App. config. O arquivo IService1 contém um contrato de serviço padrão.</span><span class="sxs-lookup"><span data-stu-id="7da03-125">Visual Studio creates the project, which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config. The IService1 file contains a default service contract.</span></span> <span data-ttu-id="7da03-126">O arquivo Service1 contém uma implementação padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="7da03-126">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="7da03-127">O arquivo App.config contém a configuração necessária para carregar o serviço padrão com o Host de Serviço WCF do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7da03-127">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="7da03-128">Para obter mais informações sobre a ferramenta de Host de serviço WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="7da03-128">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>

3. <span data-ttu-id="7da03-129">Abra o arquivo IService1.cs ou IService1.vb e exclua o código dentro da declaração de namespace, deixando a declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="7da03-129">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration, leaving the namespace declaration.</span></span> <span data-ttu-id="7da03-130">Dentro da declaração do namespace, defina uma nova interface chamada `ICalculator` conforme mostrado no código abaixo.</span><span class="sxs-lookup"><span data-stu-id="7da03-130">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>

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

     <span data-ttu-id="7da03-131">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="7da03-131">This contract defines an online calculator.</span></span> <span data-ttu-id="7da03-132">Observe que a interface do `ICalculator` está marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7da03-132">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="7da03-133">Esse atributo define um namespace que é usado para remover a ambiguidade do nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="7da03-133">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="7da03-134">Cada operação da calculadora é marcada com o atributo <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7da03-134">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7da03-135">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7da03-135">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7da03-136">Como: implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7da03-136">How to: Implement a service contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a><span data-ttu-id="7da03-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7da03-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="7da03-138">Como implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7da03-138">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="7da03-139">Introdução</span><span class="sxs-lookup"><span data-stu-id="7da03-139">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="7da03-140">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="7da03-140">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)