---
title: 'Tutorial: definir um contrato de serviço de Windows Communication Foundation'
description: Saiba como definir um contrato de serviço como parte de uma série de artigos que ajudam você a começar a criar um aplicativo WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246305"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="25e36-103">Tutorial: definir um contrato de serviço de Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="25e36-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="25e36-104">Este tutorial descreve a primeira de cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF).</span><span class="sxs-lookup"><span data-stu-id="25e36-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="25e36-105">Para obter uma visão geral dos tutoriais, consulte [tutorial: introdução aos aplicativos Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="25e36-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="25e36-106">Quando você cria um serviço WCF, sua primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="25e36-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="25e36-107">O contrato de serviço especifica a quais operações o serviço dá suporte.</span><span class="sxs-lookup"><span data-stu-id="25e36-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="25e36-108">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="25e36-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="25e36-109">Você cria contratos de serviço definindo uma interface C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="25e36-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="25e36-110">Uma interface tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="25e36-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="25e36-111">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="25e36-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="25e36-112">Para cada interface, você deve aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="25e36-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="25e36-113">Para cada operação/método, você deve aplicar o <xref:System.ServiceModel.OperationContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="25e36-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="25e36-114">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="25e36-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="25e36-115">Crie um projeto de **biblioteca de serviços WCF** .</span><span class="sxs-lookup"><span data-stu-id="25e36-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="25e36-116">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="25e36-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="25e36-117">Criar um projeto de biblioteca de serviço WCF e definir uma interface de contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="25e36-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="25e36-118">Abra o Visual Studio como administrador.</span><span class="sxs-lookup"><span data-stu-id="25e36-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="25e36-119">Para fazer isso, selecione o programa Visual Studio no menu **Iniciar** e, em seguida, selecione **mais**  >  **Executar como administrador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="25e36-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="25e36-120">Crie um projeto de **biblioteca de serviços WCF** .</span><span class="sxs-lookup"><span data-stu-id="25e36-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="25e36-121">No menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="25e36-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="25e36-122">Na caixa de diálogo **novo projeto** , no lado esquerdo, expanda **Visual C#** ou **Visual Basic**e, em seguida, selecione a categoria **WCF** .</span><span class="sxs-lookup"><span data-stu-id="25e36-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="25e36-123">O Visual Studio exibe uma lista de modelos de projeto na seção central da janela.</span><span class="sxs-lookup"><span data-stu-id="25e36-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="25e36-124">Selecione **biblioteca de serviços WCF**.</span><span class="sxs-lookup"><span data-stu-id="25e36-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="25e36-125">Se você não vir a categoria de modelo de projeto do **WCF** , talvez seja necessário instalar o componente **Windows Communication Foundation** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25e36-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="25e36-126">Na caixa de diálogo **novo projeto** , selecione o link **abrir instalador do Visual Studio** no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="25e36-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="25e36-127">Selecione a guia **componentes individuais** e, em seguida, localize e selecione **Windows Communication Foundation** na categoria **atividades de desenvolvimento** .</span><span class="sxs-lookup"><span data-stu-id="25e36-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="25e36-128">Escolha **Modificar** para começar a instalar o componente.</span><span class="sxs-lookup"><span data-stu-id="25e36-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="25e36-129">Na seção inferior da janela, digite *GettingStartedLib* para o **nome** e *gettingstarted* para o nome da **solução**.</span><span class="sxs-lookup"><span data-stu-id="25e36-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="25e36-130">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="25e36-130">Select **OK**.</span></span>

      <span data-ttu-id="25e36-131">O Visual Studio cria o projeto, que tem três arquivos *: IService1.cs* ( *ou IService1. vb* para um projeto Visual Basic), *Service1.cs* (ou *Service1. vb* para um projeto Visual Basic) e *App.config*. O Visual Studio define esses arquivos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="25e36-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="25e36-132">O arquivo *IService1* contém a definição padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="25e36-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="25e36-133">O arquivo *Service1* contém a implementação padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="25e36-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="25e36-134">O arquivo de *App.config* contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta de host do serviço WCF do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25e36-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="25e36-135">Para obter mais informações sobre a ferramenta host de serviço do WCF, consulte [host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="25e36-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="25e36-136">Se você instalou o Visual Studio com Visual Basic configurações de ambiente de desenvolvedor, a solução pode estar oculta.</span><span class="sxs-lookup"><span data-stu-id="25e36-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="25e36-137">Se esse for o caso, selecione **Opções** no menu **ferramentas** e, em seguida, selecione **projetos e soluções**  >  **geral** na janela **Opções** .</span><span class="sxs-lookup"><span data-stu-id="25e36-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="25e36-138">Selecione **sempre mostrar solução**.</span><span class="sxs-lookup"><span data-stu-id="25e36-138">Select **Always show solution**.</span></span> <span data-ttu-id="25e36-139">Além disso, verifique se **salvar novos projetos quando criado** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="25e36-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="25e36-140">Em **Gerenciador de soluções**, abra o arquivo **IService1.cs** ou **IService1. vb** e substitua seu código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="25e36-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="25e36-141">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="25e36-141">This contract defines an online calculator.</span></span> <span data-ttu-id="25e36-142">Observe que a `ICalculator` interface está marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo (simplificado como `ServiceContract` ).</span><span class="sxs-lookup"><span data-stu-id="25e36-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="25e36-143">Esse atributo define um namespace para desambiguar o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="25e36-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="25e36-144">O código marca cada operação de calculadora com o <xref:System.ServiceModel.OperationContractAttribute> atributo (simplificado como `OperationContract` ).</span><span class="sxs-lookup"><span data-stu-id="25e36-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="25e36-145">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="25e36-145">Next steps</span></span>

<span data-ttu-id="25e36-146">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="25e36-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="25e36-147">Crie um projeto de biblioteca de serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="25e36-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="25e36-148">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="25e36-148">Define a service contract interface.</span></span>

<span data-ttu-id="25e36-149">Avance para o próximo tutorial para aprender a implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="25e36-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25e36-150">Tutorial: implementar um contrato de serviço WCF</span><span class="sxs-lookup"><span data-stu-id="25e36-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
