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
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="717df-102">Tutorial: Defina um contrato de serviço da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="717df-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="717df-103">Este tutorial descreve a primeira das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="717df-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="717df-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="717df-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="717df-105">Quando você cria um serviço WCF, sua primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="717df-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="717df-106">O contrato de serviço especifica a quais operações o serviço dá suporte.</span><span class="sxs-lookup"><span data-stu-id="717df-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="717df-107">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="717df-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="717df-108">Você cria contratos de serviço definindo uma interface C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="717df-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="717df-109">Uma interface tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="717df-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="717df-110">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="717df-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="717df-111">Para cada interface, você <xref:System.ServiceModel.ServiceContractAttribute> deve aplicar o atributo.</span><span class="sxs-lookup"><span data-stu-id="717df-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="717df-112">Para cada operação/método, você <xref:System.ServiceModel.OperationContractAttribute> deve aplicar o atributo.</span><span class="sxs-lookup"><span data-stu-id="717df-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="717df-113">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="717df-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="717df-114">Crie um projeto **de Biblioteca de Serviços WCF.**</span><span class="sxs-lookup"><span data-stu-id="717df-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="717df-115">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="717df-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="717df-116">Crie um projeto de Biblioteca de Serviços WCF e defina uma interface de contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="717df-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="717df-117">Abra o Visual Studio como administrador.</span><span class="sxs-lookup"><span data-stu-id="717df-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="717df-118">Para isso, selecione o programa Visual Studio no menu **Iniciar** e selecione **Mais** > **Executar como administrador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="717df-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="717df-119">Crie um projeto **de Biblioteca de Serviços WCF.**</span><span class="sxs-lookup"><span data-stu-id="717df-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="717df-120">No menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="717df-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="717df-121">Na caixa de diálogo **Novo Projeto,** no lado esquerdo, expanda **visual C#** ou **Visual Basic**e selecione a categoria **WCF.**</span><span class="sxs-lookup"><span data-stu-id="717df-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="717df-122">O Visual Studio exibe uma lista de modelos de projeto na seção central da janela.</span><span class="sxs-lookup"><span data-stu-id="717df-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="717df-123">Selecione **biblioteca de serviços WCF**.</span><span class="sxs-lookup"><span data-stu-id="717df-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="717df-124">Se você não ver a categoria de modelo de projeto **WCF,** talvez seja necessário instalar o componente da **Windows Communication Foundation** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="717df-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="717df-125">Na caixa de diálogo **Novo Projeto,** selecione o link **Instalador do Estúdio Visual Aberto** no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="717df-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="717df-126">Selecione a guia **Componentes Individuais** e, em seguida, encontre e selecione **a Fundação de Comunicação do Windows** na categoria **Atividades de Desenvolvimento.**</span><span class="sxs-lookup"><span data-stu-id="717df-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="717df-127">Escolha **Modificar** para começar a instalar o componente.</span><span class="sxs-lookup"><span data-stu-id="717df-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="717df-128">Na seção inferior da janela, *digite GettingStartedLib* para o **nome** e *GettingStarted* para o **nome da solução**.</span><span class="sxs-lookup"><span data-stu-id="717df-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="717df-129">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="717df-129">Select **OK**.</span></span>

      <span data-ttu-id="717df-130">O Visual Studio cria o projeto, que possui três arquivos: *IService1.cs* (ou *IService1.vb* para um projeto Visual Basic), *Service1.cs* (ou *Service1.vb* para um projeto Visual Basic) e *App.config*. O Visual Studio define esses arquivos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="717df-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="717df-131">O arquivo *IService1* contém a definição padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="717df-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="717df-132">O arquivo *Service1* contém a implementação padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="717df-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="717df-133">O arquivo *App.config* contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta Visual Studio WCF Service Host.</span><span class="sxs-lookup"><span data-stu-id="717df-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="717df-134">Para obter mais informações sobre a ferramenta Host de serviço wcf, consulte [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="717df-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="717df-135">Se você instalou o Visual Studio com as configurações do ambiente de desenvolvedor Visual Basic, a solução pode estar oculta.</span><span class="sxs-lookup"><span data-stu-id="717df-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="717df-136">Se esse for o caso, selecione **Opções** no menu **Ferramentas** e selecione **Projetos e Soluções** > **Gerais** na janela **Opções.**</span><span class="sxs-lookup"><span data-stu-id="717df-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="717df-137">Selecione **Sempre mostrar solução**.</span><span class="sxs-lookup"><span data-stu-id="717df-137">Select **Always show solution**.</span></span> <span data-ttu-id="717df-138">Além disso, verifique **se salvar novos projetos quando criado sao** selecionados.</span><span class="sxs-lookup"><span data-stu-id="717df-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="717df-139">A partir **do Solution Explorer,** abra o arquivo **IService1.cs** ou **IService1.vb** e substitua seu código pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="717df-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="717df-140">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="717df-140">This contract defines an online calculator.</span></span> <span data-ttu-id="717df-141">Observe `ICalculator` que a interface <xref:System.ServiceModel.ServiceContractAttribute> está marcada `ServiceContract`com o atributo (simplificado como ).</span><span class="sxs-lookup"><span data-stu-id="717df-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="717df-142">Este atributo define um namespace para desambiguar o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="717df-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="717df-143">O código marca cada operação <xref:System.ServiceModel.OperationContractAttribute> da calculadora `OperationContract`com o atributo (simplificado como ).</span><span class="sxs-lookup"><span data-stu-id="717df-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="717df-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="717df-144">Next steps</span></span>

<span data-ttu-id="717df-145">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="717df-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="717df-146">Crie um projeto de Biblioteca de Serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="717df-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="717df-147">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="717df-147">Define a service contract interface.</span></span>

<span data-ttu-id="717df-148">Avance para o próximo tutorial para saber como implementar o contrato de serviço wcf.</span><span class="sxs-lookup"><span data-stu-id="717df-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="717df-149">Tutorial: Implementar um contrato de serviço WCF</span><span class="sxs-lookup"><span data-stu-id="717df-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
