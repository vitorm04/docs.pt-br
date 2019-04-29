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
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="ae1c0-102">Tutorial: Definir um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ae1c0-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="ae1c0-103">Este tutorial descreve o primeiro de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ae1c0-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ae1c0-105">Quando você cria um serviço WCF, a primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="ae1c0-106">O contrato de serviço especifica a quais operações os serviços dão suporte.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="ae1c0-107">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="ae1c0-108">Criar contratos de serviço com a definição de um Visual C# ou a interface do Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="ae1c0-109">Uma interface tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="ae1c0-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="ae1c0-110">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="ae1c0-111">Para cada interface, você deve aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="ae1c0-112">Para cada operação/método, você deve aplicar o <xref:System.ServiceModel.OperationContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="ae1c0-113">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="ae1c0-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ae1c0-114">Criar uma **WCF Service Library** projeto.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="ae1c0-115">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="ae1c0-116">Criar um projeto de biblioteca de serviço do WCF e definir uma interface de contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="ae1c0-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="ae1c0-117">Abra o Visual Studio como um administrador.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="ae1c0-118">Para fazer isso, selecione o programa Visual Studio na **inicie** menu e, em seguida, selecione **mais** > **executar como administrador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="ae1c0-119">Criar uma **WCF Service Library** projeto.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="ae1c0-120">No menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="ae1c0-121">No **novo projeto** caixa de diálogo, no lado esquerdo, expanda **Visual c#** ou **Visual Basic**e, em seguida, selecione o **WCF** categoria.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="ae1c0-122">Visual Studio exibe uma lista de modelos de projeto na seção central da janela.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="ae1c0-123">Selecione **WCF Service Library**.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="ae1c0-124">Se você não vir as **WCF** categoria do modelo de projeto, você talvez precise instalar o **Windows Communication Foundation** componente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="ae1c0-125">No **novo projeto** caixa de diálogo, selecione o **abrir instalador do Visual Studio** link no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="ae1c0-126">Selecione o **componentes individuais** guia e, em seguida, localize e selecione **Windows Communication Foundation** sob o **atividades de desenvolvimento** categoria.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="ae1c0-127">Escolher **modificar** para começar a instalação do componente.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="ae1c0-128">Na seção inferior da janela, digite *GettingStartedLib* para o **nome** e *GettingStarted* para o **nome da solução**.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="ae1c0-129">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-129">Select **OK**.</span></span>

      <span data-ttu-id="ae1c0-130">O Visual Studio cria o projeto, que tem três arquivos: *IService1.cs* (ou *IService1.vb* para um projeto do Visual Basic), *Service1.cs* (ou *Service1.vb* para um projeto do Visual Basic), e  *App. config*. O Visual Studio define esses arquivos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ae1c0-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="ae1c0-131">O *IService1* arquivo contém a definição padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="ae1c0-132">O *Service1* arquivo contém a implementação padrão de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="ae1c0-133">O *App. config* arquivo contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta de Host do serviço de WCF do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="ae1c0-134">Para obter mais informações sobre a ferramenta de Host de serviço WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="ae1c0-135">Se você instalou o Visual Studio com as configurações de ambiente de desenvolvedor de Visual Basic, a solução pode estar oculto.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="ae1c0-136">Se esse for o caso, selecione **opções** da **ferramentas** menu, em seguida, selecione **projetos e soluções** > **geral** em o **opções** janela.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="ae1c0-137">Selecione **sempre mostrar solução**.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-137">Select **Always show solution**.</span></span> <span data-ttu-id="ae1c0-138">Além disso, verifique **salvar novos projetos quando criados** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="ae1c0-139">Partir **Gerenciador de soluções**, abra o **IService1.cs** ou **IService1.vb** de arquivo e substitua seu código com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ae1c0-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="ae1c0-140">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-140">This contract defines an online calculator.</span></span> <span data-ttu-id="ae1c0-141">Observe que o `ICalculator` interface é marcado com o <xref:System.ServiceModel.ServiceContractAttribute> atributo (simplificada como `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="ae1c0-142">Este atributo define um namespace para desambiguar o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="ae1c0-143">O código marca cada operação da Calculadora com o <xref:System.ServiceModel.OperationContractAttribute> atributo (simplificada como `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae1c0-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ae1c0-144">Next steps</span></span>

<span data-ttu-id="ae1c0-145">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="ae1c0-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ae1c0-146">Crie um projeto de biblioteca de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="ae1c0-147">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-147">Define a service contract interface.</span></span>

<span data-ttu-id="ae1c0-148">Avance para o próximo tutorial para aprender a implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae1c0-149">Tutorial: Implementar um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="ae1c0-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
