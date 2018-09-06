---
title: 'Instruções passo a passo: criando um aplicativo extensível'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875090"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="6112c-102">Instruções passo a passo: criando um aplicativo extensível</span><span class="sxs-lookup"><span data-stu-id="6112c-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="6112c-103">Este passo a passo descreve como criar um pipeline para um suplemento que executa funções de calculadora simples.</span><span class="sxs-lookup"><span data-stu-id="6112c-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="6112c-104">Ele não Demonstre um cenário do mundo real; em vez disso, ele demonstra a funcionalidade básica de um pipeline e como um suplemento pode fornecer serviços para um host.</span><span class="sxs-lookup"><span data-stu-id="6112c-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="6112c-105">Este passo a passo descreve as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="6112c-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="6112c-106">Criando uma solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="6112c-107">Criando a estrutura de diretórios de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6112c-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="6112c-108">Criando o contrato e modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="6112c-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="6112c-109">Criando o adaptador do lado do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="6112c-110">Criando o adaptador do lado do host.</span><span class="sxs-lookup"><span data-stu-id="6112c-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="6112c-111">Criando o host.</span><span class="sxs-lookup"><span data-stu-id="6112c-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="6112c-112">Criando o suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="6112c-113">Implantando o pipeline.</span><span class="sxs-lookup"><span data-stu-id="6112c-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="6112c-114">Executando o aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="6112c-114">Running the host application.</span></span>  
  
 <span data-ttu-id="6112c-115">Esse pipeline passa apenas tipos serializáveis (<xref:System.Double> e <xref:System.String>), entre o host e o suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="6112c-116">Para obter um exemplo que mostra como passar coleções de tipos de dados complexos, consulte [instruções passo a passo: passando coleções entre Hosts e suplementos](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="6112c-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="6112c-117">O contrato para este pipeline define um modelo de objeto das quatro operações aritméticas: adicionar, subtrair, multiplicar e dividir.</span><span class="sxs-lookup"><span data-stu-id="6112c-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="6112c-118">O host fornece o suplemento com uma equação para calcular como 2 + 2, e o suplemento retorna o resultado para o host.</span><span class="sxs-lookup"><span data-stu-id="6112c-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="6112c-119">Versão 2 do suplemento Calculadora fornece o cálculo mais possibilidades e demonstra o controle de versão.</span><span class="sxs-lookup"><span data-stu-id="6112c-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="6112c-120">Ele é descrito em [instruções passo a passo: Habilitando a compatibilidade com versões anteriores como seu Host é alterado](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="6112c-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6112c-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6112c-121">Prerequisites</span></span>  
 <span data-ttu-id="6112c-122">Você precisa dos seguintes itens para concluir esta explicação:</span><span class="sxs-lookup"><span data-stu-id="6112c-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="6112c-123">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="6112c-124">Criando uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6112c-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="6112c-125">Use uma solução no Visual Studio para conter os projetos os segmentos de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6112c-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="6112c-126">Para criar a solução do pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="6112c-127">No Visual Studio, crie um novo projeto chamado `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="6112c-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="6112c-128">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-129">Nomeie a solução `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="6112c-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="6112c-130">Criando a estrutura de diretórios de Pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="6112c-131">O modelo de suplemento exige os assemblies do segmento de pipeline sejam colocados em uma estrutura de diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6112c-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="6112c-132">Para obter mais informações sobre a estrutura de pipeline, consulte [requisitos de desenvolvimento de Pipeline](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="6112c-132">For more information about the pipeline structure, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="6112c-133">Para criar a estrutura de diretórios de pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="6112c-134">Crie uma pasta de aplicativo em qualquer lugar no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6112c-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="6112c-135">Nessa pasta, crie a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="6112c-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="6112c-136">Não é necessário colocar a estrutura de pastas do pipeline na pasta do aplicativo; Isso é feito aqui apenas para conveniência.</span><span class="sxs-lookup"><span data-stu-id="6112c-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="6112c-137">A etapa apropriado, o passo a passo explica como alterar o código quando a estrutura de pastas do pipeline está em um local diferente.</span><span class="sxs-lookup"><span data-stu-id="6112c-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="6112c-138">Veja a discussão de requisitos de diretório do pipeline na [requisitos de desenvolvimento de Pipeline](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="6112c-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6112c-139">O `CalcV2` pasta não é usada neste passo a passo; ele é um espaço reservado [passo a passo: Habilitando a compatibilidade com versões anteriores como seu Host é alterado](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="6112c-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="6112c-140">Criando o contrato e modos de exibição</span><span class="sxs-lookup"><span data-stu-id="6112c-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="6112c-141">O segmento de contrato para este pipeline define o `ICalc1Contract` interface, que define quatro métodos: `add`, `subtract`, `multiply`, e `divide`.</span><span class="sxs-lookup"><span data-stu-id="6112c-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="6112c-142">Para criar um contrato</span><span class="sxs-lookup"><span data-stu-id="6112c-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="6112c-143">Na solução do Visual Studio denominada `CalculatorV1`, abra o `Calc1Contract` projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="6112c-144">Na **Gerenciador de soluções**, adicione referências aos assemblies a seguir para o `Calc1Contract` projeto:</span><span class="sxs-lookup"><span data-stu-id="6112c-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="6112c-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="6112c-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="6112c-147">Na **Gerenciador de soluções**, excluir a classe padrão que é adicionada a new **biblioteca de classes** projetos.</span><span class="sxs-lookup"><span data-stu-id="6112c-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="6112c-148">Na **Gerenciador de soluções**, adicione um novo item ao projeto, usando o **Interface** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="6112c-149">No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="6112c-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="6112c-150">No arquivo de interface, adicione referências a namespace <xref:System.AddIn.Contract> e <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="6112c-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="6112c-151">Use o código a seguir para concluir este segmento de contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="6112c-152">Observe que essa interface deve ter o <xref:System.AddIn.Pipeline.AddInContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="6112c-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="6112c-153">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="6112c-154">A solução não pode ser executada até que o procedimento final, mas criá-lo depois de cada procedimento garante que cada projeto é corrigir.</span><span class="sxs-lookup"><span data-stu-id="6112c-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="6112c-155">Porque o modo de exibição e o host do modo de exibição de suplemento geralmente têm o mesmo código, especialmente na primeira versão de um suplemento, você pode criar facilmente os modos de exibição ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="6112c-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="6112c-156">Eles diferem por apenas um fator: o modo de exibição requer a <xref:System.AddIn.Pipeline.AddInBaseAttribute> de atributo, embora a exibição do suplemento do host não exija que todos os atributos.</span><span class="sxs-lookup"><span data-stu-id="6112c-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="6112c-157">Para criar o modo de exibição</span><span class="sxs-lookup"><span data-stu-id="6112c-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="6112c-158">Adicionar um novo projeto chamado `Calc1AddInView` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-159">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-160">Na **Gerenciador de soluções**, adicione uma referência ao System.AddIn.dll para o `Calc1AddInView` projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="6112c-161">Na **Gerenciador de soluções**, excluir a classe padrão que é adicionada a new **biblioteca de classes** projetos e adicionar um novo item ao projeto, usando o **Interface** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="6112c-162">No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="6112c-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="6112c-163">No arquivo de interface, adicione uma referência ao namespace para <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="6112c-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="6112c-164">Use o código a seguir para concluir este modo de exibição do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="6112c-165">Observe que essa interface deve ter o <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="6112c-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="6112c-166">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="6112c-167">Para criar a exibição do suplemento do host</span><span class="sxs-lookup"><span data-stu-id="6112c-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="6112c-168">Adicionar um novo projeto chamado `Calc1HVA` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-169">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-170">Na **Gerenciador de soluções**, excluir a classe padrão que é adicionada a new **biblioteca de classes** projetos e adicionar um novo item ao projeto, usando o **Interface** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="6112c-171">No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="6112c-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="6112c-172">No arquivo de interface, use o código a seguir para concluir a exibição do suplemento do host.</span><span class="sxs-lookup"><span data-stu-id="6112c-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="6112c-173">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="6112c-174">Criação do adaptador de adicionar lado</span><span class="sxs-lookup"><span data-stu-id="6112c-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="6112c-175">Esse adaptador adicionar lado consiste em um adaptador de exibição-para-contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="6112c-176">Este segmento de pipeline converte os tipos da exibição do suplemento do contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="6112c-177">Nesse pipeline, o suplemento fornece um serviço para o host e os tipos de fluxo do suplemento ao host.</span><span class="sxs-lookup"><span data-stu-id="6112c-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="6112c-178">Porque não há tipos de fluxo do host para o suplemento, você não precisa incluir um adaptador de contrato para exibição no lado do suplemento desse pipeline.</span><span class="sxs-lookup"><span data-stu-id="6112c-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="6112c-179">Para criar o adaptador do lado do suplemento</span><span class="sxs-lookup"><span data-stu-id="6112c-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="6112c-180">Adicionar um novo projeto chamado `Calc1AddInSideAdapter` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-181">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-182">Na **Gerenciador de soluções**, adicione referências aos assemblies a seguir para o `Calc1AddInSideAdapter` projeto:</span><span class="sxs-lookup"><span data-stu-id="6112c-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="6112c-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="6112c-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="6112c-185">Adicione referências de projeto para os projetos para os segmentos de pipeline adjacentes:</span><span class="sxs-lookup"><span data-stu-id="6112c-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="6112c-186">Selecione cada referência de projeto e, na **propriedades** defina **Copy Local** para **False**.</span><span class="sxs-lookup"><span data-stu-id="6112c-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="6112c-187">No Visual Basic, use o **referências** guia de **propriedades do projeto** para definir **Copy Local** para **False** para as duas referências de projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="6112c-188">Renomeie a classe do projeto padrão `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="6112c-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="6112c-189">No arquivo de classe, adicione referências a namespace <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="6112c-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="6112c-190">No arquivo de classe, adicione referências de namespace para os segmentos adjacentes: `CalcAddInViews` e `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="6112c-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="6112c-191">(No Visual Basic, essas referências de namespace são `Calc1AddInView.CalcAddInViews` e `Calc1Contract.CalculatorContracts`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="6112c-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="6112c-192">Aplicar a <xref:System.AddIn.Pipeline.AddInAdapterAttribute> de atributo para o `CalculatorViewToContractAddInSideAdapter` classe para identificá-lo como o adaptador do lado do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="6112c-193">Verifique a `CalculatorViewToContractAddInSideAdapter` herdam da classe <xref:System.AddIn.Pipeline.ContractBase>, que fornece uma implementação padrão da <xref:System.AddIn.Contract.IContract> interface e implementa a interface de contrato para o pipeline, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="6112c-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="6112c-194">Adicione um construtor público que aceita um `ICalculator`, armazena em cache em um campo particular e chama o construtor de classe base.</span><span class="sxs-lookup"><span data-stu-id="6112c-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="6112c-195">Para implementar os membros da `ICalc1Contract`, basta chamar os membros correspondentes da `ICalculator` instância que é passada para o construtor e retorna os resultados.</span><span class="sxs-lookup"><span data-stu-id="6112c-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="6112c-196">Isso se adapta o modo de exibição (`ICalculator`) para o contrato (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="6112c-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="6112c-197">O código a seguir mostra o adaptador de adicionar lado do suplemento concluído.</span><span class="sxs-lookup"><span data-stu-id="6112c-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="6112c-198">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="6112c-199">Criando o adaptador do lado do Host</span><span class="sxs-lookup"><span data-stu-id="6112c-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="6112c-200">Esse adaptador do lado do host consiste em um adaptador de contrato para exibição.</span><span class="sxs-lookup"><span data-stu-id="6112c-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="6112c-201">Este segmento se adapta o contrato para o modo de host do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="6112c-202">Nesse pipeline, o suplemento fornece um serviço para o host e o fluxo de tipos de suplemento para o host.</span><span class="sxs-lookup"><span data-stu-id="6112c-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="6112c-203">Porque não há tipos de fluxo do host para o suplemento, você não precisa incluir um adaptador de exibição-para-contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="6112c-204">Para implementar o gerenciamento de tempo de vida, use um <xref:System.AddIn.Pipeline.ContractHandle> objeto a ser anexado a um token de tempo de vida do contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="6112c-205">Você deve manter uma referência a esse identificador na ordem para o gerenciamento de tempo de vida trabalhar.</span><span class="sxs-lookup"><span data-stu-id="6112c-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="6112c-206">Depois que o token é aplicado, nenhuma programação adicional é necessária porque o suplemento do sistema pode descartar objetos quando eles não estão sendo usados e torná-los disponíveis para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6112c-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="6112c-207">Para obter mais informações, consulte [gerenciamento de tempo de vida](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="6112c-207">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="6112c-208">Para criar o adaptador do lado do host</span><span class="sxs-lookup"><span data-stu-id="6112c-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="6112c-209">Adicionar um novo projeto chamado `Calc1HostSideAdapter` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-210">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-211">Na **Gerenciador de soluções**, adicione referências aos assemblies a seguir para o `Calc1HostSideAdapter` projeto:</span><span class="sxs-lookup"><span data-stu-id="6112c-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="6112c-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="6112c-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="6112c-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="6112c-214">Adicione referências de projeto para os projetos para os segmentos adjacentes:</span><span class="sxs-lookup"><span data-stu-id="6112c-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="6112c-215">Selecione cada referência de projeto e, na **propriedades** defina **Copy Local** para **False**.</span><span class="sxs-lookup"><span data-stu-id="6112c-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="6112c-216">No Visual Basic, use o **referências** guia de **propriedades do projeto** para definir **Copy Local** para **False** para as duas referências de projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="6112c-217">Renomeie a classe do projeto padrão `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="6112c-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="6112c-218">No arquivo de classe, adicione referências a namespace <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="6112c-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="6112c-219">No arquivo de classe, adicione referências de namespace para os segmentos adjacentes: `CalcHVAs` e `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="6112c-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="6112c-220">(No Visual Basic, essas referências de namespace são `Calc1HVA.CalcHVAs` e `Calc1Contract.CalculatorContracts`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="6112c-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="6112c-221">Aplicar a <xref:System.AddIn.Pipeline.HostAdapterAttribute> de atributo para o `CalculatorContractToViewHostSideAdapter` classe para identificá-lo como o segmento de adaptador do lado do host.</span><span class="sxs-lookup"><span data-stu-id="6112c-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="6112c-222">Verifique as `CalculatorContractToViewHostSideAdapter` classe implementa a interface que representa a exibição do suplemento do host: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6112c-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="6112c-223">Adicione um construtor público que aceita o tipo de contrato de pipeline, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="6112c-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="6112c-224">O construtor deve armazenar em cache a referência ao contrato.</span><span class="sxs-lookup"><span data-stu-id="6112c-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="6112c-225">Ele também deve criar e armazenar em cache um novo <xref:System.AddIn.Pipeline.ContractHandle> para o contrato, para gerenciar a vida útil do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6112c-226">O <xref:System.AddIn.Pipeline.ContractHandle> é essencial ao gerenciamento de tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="6112c-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="6112c-227">Se você não conseguir manter uma referência para o <xref:System.AddIn.Pipeline.ContractHandle> de objetos, coleta de lixo será solicitá-lo e o pipeline será desligado quando o seu programa não espera.</span><span class="sxs-lookup"><span data-stu-id="6112c-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="6112c-228">Isso pode levar a erros que são difíceis de diagnosticar, tais como <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="6112c-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="6112c-229">Desligamento é um estágio normal na vida de um pipeline, portanto, não há nenhuma maneira para o código de tempo de vida de gerenciamento detectar essa condição é um erro.</span><span class="sxs-lookup"><span data-stu-id="6112c-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="6112c-230">Para implementar os membros da `ICalculator`, basta chamar os membros correspondentes da `ICalc1Contract` instância que é passada para o construtor e retorna os resultados.</span><span class="sxs-lookup"><span data-stu-id="6112c-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="6112c-231">Isso se adapta o contrato (`ICalc1Contract`) para o modo de exibição (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="6112c-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="6112c-232">O código a seguir mostra o adaptador do lado do host concluído.</span><span class="sxs-lookup"><span data-stu-id="6112c-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="6112c-233">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="6112c-234">Criando o Host</span><span class="sxs-lookup"><span data-stu-id="6112c-234">Creating the Host</span></span>  
 <span data-ttu-id="6112c-235">Um aplicativo host interage com o suplemento por meio da exibição de host do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="6112c-236">Ele usa o suplemento para detecção e ativação métodos fornecidos pelo <xref:System.AddIn.Hosting.AddInStore> e <xref:System.AddIn.Hosting.AddInToken> classes para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6112c-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="6112c-237">Atualize o cache de informações de pipeline e o suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="6112c-238">Localizar suplementos do tipo de exibição de host, `ICalculator`, sob o diretório raiz do pipeline especificado.</span><span class="sxs-lookup"><span data-stu-id="6112c-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="6112c-239">Solicita que o usuário especifique qual suplemento para usar.</span><span class="sxs-lookup"><span data-stu-id="6112c-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="6112c-240">Ative o suplemento selecionado em um novo domínio de aplicativo com um nível de confiança de segurança especificado.</span><span class="sxs-lookup"><span data-stu-id="6112c-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="6112c-241">Execute o personalizado `RunCalculator` método, que chama os métodos do suplemento, conforme especificado pela exibição de host do suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="6112c-242">Para criar o host</span><span class="sxs-lookup"><span data-stu-id="6112c-242">To create the host</span></span>  
  
1.  <span data-ttu-id="6112c-243">Adicionar um novo projeto chamado `Calc1Host` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-244">Baseá-la na **aplicativo de Console** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="6112c-245">Na **Gerenciador de soluções**, adicione uma referência ao assembly System.AddIn.dll para o `Calc1Host` projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="6112c-246">Adicione uma referência de projeto para o `Calc1HVA` projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="6112c-247">Selecione a referência de projeto e, na **propriedades** defina **Copy Local** para **False**.</span><span class="sxs-lookup"><span data-stu-id="6112c-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="6112c-248">No Visual Basic, use o **referências** guia de **propriedades do projeto** para definir **Copy Local** para **False**.</span><span class="sxs-lookup"><span data-stu-id="6112c-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="6112c-249">Renomeie o arquivo de classe (módulo no Visual Basic) `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="6112c-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="6112c-250">No Visual Basic, use o **Application** guia da **propriedades do projeto** caixa de diálogo para definir **objeto de inicialização** para **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="6112c-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="6112c-251">No arquivo de classe ou um módulo, adicione uma referência ao namespace para <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="6112c-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="6112c-252">No arquivo de classe ou um módulo, adicione uma referência de namespace para a exibição do suplemento do host: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="6112c-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="6112c-253">(No Visual Basic, esta referência de namespace é `Calc1HVA.CalcHVAs`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="6112c-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="6112c-254">No **Gerenciador de soluções**, selecione a solução e para o **Project** menu escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6112c-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="6112c-255">No **páginas de propriedade da solução** caixa de diálogo, defina as **único projeto de inicialização** ser esse projeto de aplicativo de host.</span><span class="sxs-lookup"><span data-stu-id="6112c-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="6112c-256">No arquivo de classe ou um módulo, use o <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> método para atualizar o cache.</span><span class="sxs-lookup"><span data-stu-id="6112c-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="6112c-257">Use o <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> método para obter uma coleção de tokens e use o <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> método para ativar um suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="6112c-258">O código a seguir mostra o aplicativo de host completo.</span><span class="sxs-lookup"><span data-stu-id="6112c-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6112c-259">Esse código supõe que a estrutura de pastas de pipeline está localizada na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6112c-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="6112c-260">Se você localizá-lo em outro lugar, altere a linha de código que define o `addInRoot` variável, para que a variável contém o caminho para a sua estrutura de diretório do pipeline.</span><span class="sxs-lookup"><span data-stu-id="6112c-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="6112c-261">O código usa um `ChooseCalculator` método para listar os tokens e solicitar ao usuário escolher um suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="6112c-262">O `RunCalculator` método solicita ao usuário para expressões matemáticas simples, analisa as expressões que usam o `Parser` classe e exibe os resultados retornados pelo suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="6112c-263">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="6112c-264">Criando o suplemento</span><span class="sxs-lookup"><span data-stu-id="6112c-264">Creating the Add-In</span></span>  
 <span data-ttu-id="6112c-265">Um suplemento implementa os métodos especificados pela exibição de suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="6112c-266">Esse suplemento implementa o `Add`, `Subtract`, `Multiply`, e `Divide` operações e retorna os resultados para o host.</span><span class="sxs-lookup"><span data-stu-id="6112c-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="6112c-267">Para criar o suplemento</span><span class="sxs-lookup"><span data-stu-id="6112c-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="6112c-268">Adicionar um novo projeto chamado `AddInCalcV1` para o `CalculatorV1` solução.</span><span class="sxs-lookup"><span data-stu-id="6112c-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="6112c-269">Baseá-la na **biblioteca de classes** modelo.</span><span class="sxs-lookup"><span data-stu-id="6112c-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="6112c-270">Na **Gerenciador de soluções**, adicione uma referência ao assembly System.AddIn.dll ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="6112c-271">Adicione uma referência de projeto para o `Calc1AddInView` projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="6112c-272">Selecione a referência de projeto e, na **propriedades**, defina **Copy Local** para **False**.</span><span class="sxs-lookup"><span data-stu-id="6112c-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="6112c-273">No Visual Basic, use o **referências** guia de **propriedades do projeto** para definir **Copy Local** para **False** para a referência de projeto.</span><span class="sxs-lookup"><span data-stu-id="6112c-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="6112c-274">Renomeie a classe `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="6112c-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="6112c-275">No arquivo de classe, adicione uma referência ao namespace para <xref:System.AddIn> e o segmento de exibição do suplemento: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6112c-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="6112c-276">Aplicar a <xref:System.AddIn.AddInAttribute> de atributo para o `AddInCalcV1` classe, para identificar a classe como um suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="6112c-277">Verifique as `AddInCalcV1` classe implementa a interface que representa o modo de exibição: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6112c-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="6112c-278">Implementar os membros da `ICalculator` , retornando os resultados dos cálculos apropriados.</span><span class="sxs-lookup"><span data-stu-id="6112c-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="6112c-279">O código a seguir mostra o suplemento concluído.</span><span class="sxs-lookup"><span data-stu-id="6112c-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="6112c-280">Opcionalmente, compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="6112c-281">Implantar o Pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="6112c-282">Agora você está pronto para compilar e implantar os segmentos de suplemento para a estrutura de diretórios de pipeline necessários.</span><span class="sxs-lookup"><span data-stu-id="6112c-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="6112c-283">Para implantar os segmentos de pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="6112c-284">Para cada projeto na solução, use o **construir** guia de **propriedades do projeto** (o **compilar** guia no Visual Basic) para definir o valor da **caminho de saída**  (o **caminho de saída de compilação** no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6112c-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="6112c-285">Se você nomeou sua pasta do aplicativo `MyApp`, por exemplo, seus projetos compilaria nas seguintes pastas:</span><span class="sxs-lookup"><span data-stu-id="6112c-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="6112c-286">Projeto</span><span class="sxs-lookup"><span data-stu-id="6112c-286">Project</span></span>|<span data-ttu-id="6112c-287">Caminho</span><span class="sxs-lookup"><span data-stu-id="6112c-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="6112c-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="6112c-288">AddInCalcV1</span></span>|<span data-ttu-id="6112c-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="6112c-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="6112c-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="6112c-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="6112c-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="6112c-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="6112c-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="6112c-292">Calc1AddInView</span></span>|<span data-ttu-id="6112c-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="6112c-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="6112c-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="6112c-294">Calc1Contract</span></span>|<span data-ttu-id="6112c-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="6112c-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="6112c-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="6112c-296">Calc1Host</span></span>|<span data-ttu-id="6112c-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="6112c-297">MyApp</span></span>|  
    |<span data-ttu-id="6112c-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="6112c-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="6112c-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="6112c-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="6112c-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="6112c-300">Calc1HVA</span></span>|<span data-ttu-id="6112c-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="6112c-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="6112c-302">Se você decidiu colocar sua estrutura de pasta de pipeline em um local diferente da sua pasta do aplicativo, você deve modificar os caminhos mostrados na tabela adequadamente.</span><span class="sxs-lookup"><span data-stu-id="6112c-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="6112c-303">Veja a discussão de requisitos de diretório do pipeline na [requisitos de desenvolvimento de Pipeline](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="6112c-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="6112c-304">Compile a solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6112c-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="6112c-305">Verifique os diretórios de pipeline e de aplicativo para garantir que os assemblies foram copiados nos diretórios corretos e que não há cópias extras dos assemblies foram instaladas nas pastas de errado.</span><span class="sxs-lookup"><span data-stu-id="6112c-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6112c-306">Se você não alterou **Copy Local** para **falso** para o `Calc1AddInView` referência no projeto de `AddInCalcV1` projeto, problemas de contexto do carregador impede que o suplemento que está sendo localizado.</span><span class="sxs-lookup"><span data-stu-id="6112c-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="6112c-307">Para obter informações sobre como implantar o pipeline, consulte [requisitos de desenvolvimento de Pipeline](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="6112c-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="6112c-308">Executando o aplicativo de Host</span><span class="sxs-lookup"><span data-stu-id="6112c-308">Running the Host Application</span></span>  
 <span data-ttu-id="6112c-309">Agora você está pronto para executar o host e interagir com o suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="6112c-310">Para executar o aplicativo de host</span><span class="sxs-lookup"><span data-stu-id="6112c-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="6112c-311">No prompt de comando, vá para o diretório do aplicativo e execute o aplicativo host, `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="6112c-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="6112c-312">O host localiza todos os suplementos disponíveis de seu tipo e solicita que você selecione um suplemento.</span><span class="sxs-lookup"><span data-stu-id="6112c-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="6112c-313">Insira **1** para o suplemento só está disponível.</span><span class="sxs-lookup"><span data-stu-id="6112c-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="6112c-314">Insira uma equação para a Calculadora, como **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="6112c-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="6112c-315">Deve haver espaços entre os números e o operador.</span><span class="sxs-lookup"><span data-stu-id="6112c-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="6112c-316">Tipo de **saia** e pressione a **Enter** tecla para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6112c-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6112c-317">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6112c-317">See Also</span></span>  
 [<span data-ttu-id="6112c-318">Passo a passo: Habilitando a compatibilidade com versões anteriores como o Host é alterado</span><span class="sxs-lookup"><span data-stu-id="6112c-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="6112c-319">Passo a passo: Passando coleções entre Hosts e suplementos</span><span class="sxs-lookup"><span data-stu-id="6112c-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="6112c-320">Requisitos de desenvolvimento de pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-320">Pipeline Development Requirements</span></span>](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="6112c-321">Contratos, exibições e adaptadores</span><span class="sxs-lookup"><span data-stu-id="6112c-321">Contracts, Views, and Adapters</span></span>](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="6112c-322">Desenvolvimento de pipeline</span><span class="sxs-lookup"><span data-stu-id="6112c-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
