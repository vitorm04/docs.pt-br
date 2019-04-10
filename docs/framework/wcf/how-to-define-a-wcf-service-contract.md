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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228387"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="ebb40-102">Tutorial: Definir um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ebb40-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="ebb40-103">Este tutorial descreve o primeiro de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ebb40-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ebb40-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ebb40-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ebb40-105">Quando você cria um serviço WCF, a primeira tarefa é definir um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebb40-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="ebb40-106">O contrato de serviço especifica a quais operações os serviços dão suporte.</span><span class="sxs-lookup"><span data-stu-id="ebb40-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="ebb40-107">Uma operação pode ser considerada como um método de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ebb40-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="ebb40-108">Criar contratos de serviço com a definição de um Visual C# ou a interface do Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="ebb40-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="ebb40-109">Uma interface tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="ebb40-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="ebb40-110">Cada método na interface corresponde a uma operação de serviço específica.</span><span class="sxs-lookup"><span data-stu-id="ebb40-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="ebb40-111">Para cada interface, você deve aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ebb40-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="ebb40-112">Para cada operação/método, você deve aplicar o <xref:System.ServiceModel.OperationContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ebb40-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="ebb40-113">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="ebb40-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ebb40-114">Criar uma **WCF Service Library** projeto.</span><span class="sxs-lookup"><span data-stu-id="ebb40-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="ebb40-115">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebb40-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="ebb40-116">Criar um projeto de biblioteca de serviço do WCF e definir uma interface de contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="ebb40-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="ebb40-117">Abra o Visual Studio como um administrador.</span><span class="sxs-lookup"><span data-stu-id="ebb40-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="ebb40-118">Para fazer isso, selecione o programa Visual Studio na **inicie** menu e, em seguida, selecione **mais** > **executar como administrador** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="ebb40-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="ebb40-119">Criar uma **WCF Service Library** projeto.</span><span class="sxs-lookup"><span data-stu-id="ebb40-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="ebb40-120">No menu **Arquivo**, selecione **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ebb40-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="ebb40-121">No **novo projeto** caixa de diálogo, no lado esquerdo, expanda **Visual c#** ou **Visual Basic**e, em seguida, selecione o **WCF** categoria.</span><span class="sxs-lookup"><span data-stu-id="ebb40-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="ebb40-122">Visual Studio exibe uma lista de modelos de projeto na seção central da janela.</span><span class="sxs-lookup"><span data-stu-id="ebb40-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="ebb40-123">Selecione **WCF Service Library**.</span><span class="sxs-lookup"><span data-stu-id="ebb40-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="ebb40-124">Se você não vir as **WCF** categoria do modelo de projeto, você talvez precise instalar o **Windows Communication Foundation** componente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebb40-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="ebb40-125">No **novo projeto** caixa de diálogo, selecione o **abrir instalador do Visual Studio** link no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="ebb40-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="ebb40-126">Selecione o **componentes individuais** guia e, em seguida, localize e selecione **Windows Communication Foundation** sob o **atividades de desenvolvimento** categoria.</span><span class="sxs-lookup"><span data-stu-id="ebb40-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="ebb40-127">Escolher **modificar** para começar a instalação do componente.</span><span class="sxs-lookup"><span data-stu-id="ebb40-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="ebb40-128">Na seção inferior da janela, digite *GettingStartedLib* para o **nome** e *GettingStarted* para o **nome da solução**.</span><span class="sxs-lookup"><span data-stu-id="ebb40-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="ebb40-129">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="ebb40-129">Select **OK**.</span></span>

      <span data-ttu-id="ebb40-130">O Visual Studio cria o projeto, que tem três arquivos: *IService1.cs* (ou *IService1.vb* para um projeto do Visual Basic), *Service1.cs* (ou *Service1.vb* para um projeto do Visual Basic), e  *App. config*. O Visual Studio define esses arquivos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ebb40-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="ebb40-131">O *IService1* arquivo contém a definição padrão do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebb40-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="ebb40-132">O *Service1* arquivo contém a implementação padrão de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebb40-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="ebb40-133">O *App. config* arquivo contém as informações de configuração necessárias para carregar o serviço padrão com a ferramenta de Host do serviço de WCF do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebb40-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="ebb40-134">Para obter mais informações sobre a ferramenta de Host de serviço WCF, consulte [Host de serviço do WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ebb40-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="ebb40-135">Se você instalou o Visual Studio com as configurações de ambiente de desenvolvedor de Visual Basic, a solução pode estar oculto.</span><span class="sxs-lookup"><span data-stu-id="ebb40-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="ebb40-136">Se esse for o caso, selecione **opções** da **ferramentas** menu, em seguida, selecione **projetos e soluções** > **geral** em o **opções** janela.</span><span class="sxs-lookup"><span data-stu-id="ebb40-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="ebb40-137">Selecione **sempre mostrar solução**.</span><span class="sxs-lookup"><span data-stu-id="ebb40-137">Select **Always show solution**.</span></span> <span data-ttu-id="ebb40-138">Além disso, verifique **salvar novos projetos quando criados** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="ebb40-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="ebb40-139">Partir **Gerenciador de soluções**, abra o **IService1.cs** ou **IService1.vb** de arquivo e substitua seu código com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ebb40-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="ebb40-140">Este contrato define uma calculadora online.</span><span class="sxs-lookup"><span data-stu-id="ebb40-140">This contract defines an online calculator.</span></span> <span data-ttu-id="ebb40-141">Observe que o `ICalculator` interface é marcado com o <xref:System.ServiceModel.ServiceContractAttribute> atributo (simplificada como `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="ebb40-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="ebb40-142">Este atributo define um namespace para desambiguar o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="ebb40-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="ebb40-143">O código marca cada operação da Calculadora com o <xref:System.ServiceModel.OperationContractAttribute> atributo (simplificada como `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="ebb40-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ebb40-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ebb40-144">Next steps</span></span>

<span data-ttu-id="ebb40-145">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="ebb40-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="ebb40-146">Crie um projeto de biblioteca de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ebb40-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="ebb40-147">Defina uma interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebb40-147">Define a service contract interface.</span></span>

<span data-ttu-id="ebb40-148">Avance para o próximo tutorial para aprender a implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="ebb40-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ebb40-149">Tutorial: Implementar um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="ebb40-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
