---
title: 'Como: criar um serviço de fluxo de trabalho que consome um contrato de serviço existente'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: f25e71aec03f9808b3263f0353328f92888ccc69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962310"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="53e5d-102">Como: criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="53e5d-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="53e5d-103">.NET Framework 4,5 oferece uma integração melhor entre os serviços Web e os fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="53e5d-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="53e5d-104">A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro.</span><span class="sxs-lookup"><span data-stu-id="53e5d-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="53e5d-105">A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato.</span><span class="sxs-lookup"><span data-stu-id="53e5d-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53e5d-106">Este tópico fornece orientação passo a passo sobre como criar um serviço de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="53e5d-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="53e5d-107">Para obter mais informações sobre o desenvolvimento do serviço de fluxo de trabalho do primeiro contrato, consulte [contratar primeiro o desenvolvimento do serviço de fluxo de trabalho](contract-first-workflow-service-development.md)</span><span class="sxs-lookup"><span data-stu-id="53e5d-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="53e5d-108">Criando o projeto de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="53e5d-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="53e5d-109">No Visual Studio, selecione **arquivo**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="53e5d-110">Selecione o nó **WCF** sob o **C#** nó na árvore **modelos** e selecione o modelo **aplicativo de serviço de fluxo de trabalho WCF** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="53e5d-111">Nomeie o novo projeto `ContractFirst` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="53e5d-112">Criando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="53e5d-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="53e5d-113">Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecione **Adicionar**, **novo item...** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="53e5d-114">Selecione o nó de **código** à esquerda e o modelo de **classe** à direita.</span><span class="sxs-lookup"><span data-stu-id="53e5d-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="53e5d-115">Nomeie a nova classe `IBookService` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="53e5d-116">Na parte superior da janela de código que aparece, adicione uma instrução Using a `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="53e5d-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="53e5d-117">Altere a definição de classe de exemplo à seguinte definição da interface.</span><span class="sxs-lookup"><span data-stu-id="53e5d-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="53e5d-118">Crie o projeto pressionando **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="53e5d-119">Importando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="53e5d-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="53e5d-120">Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecione **importar contrato de serviço**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="53e5d-121">**Em\<> do projeto atual**, abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="53e5d-122">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="53e5d-123">Uma caixa de diálogo abrirá, alertando-o de que a operação foi concluída com êxito e que as atividades geradas serão exibidas na caixa de ferramentas depois que você compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="53e5d-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="53e5d-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="53e5d-125">Crie o projeto pressionando **Ctrl + Shift + B**para que as atividades importadas apareçam na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="53e5d-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="53e5d-126">Em **Gerenciador de soluções**, abra Service1. xamlx.</span><span class="sxs-lookup"><span data-stu-id="53e5d-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="53e5d-127">O serviço de fluxo de trabalho aparecerá no designer.</span><span class="sxs-lookup"><span data-stu-id="53e5d-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="53e5d-128">Selecione a atividade **sequência** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="53e5d-129">Na janela Propriedades, clique em **...**</span><span class="sxs-lookup"><span data-stu-id="53e5d-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="53e5d-130">na propriedade **ImplementedContract** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="53e5d-131">Na janela do **Editor de coleção de tipos** que aparece, clique na lista suspensa **tipo** e selecione **procurar tipos...**</span><span class="sxs-lookup"><span data-stu-id="53e5d-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="53e5d-132">inicial.</span><span class="sxs-lookup"><span data-stu-id="53e5d-132">entry.</span></span> <span data-ttu-id="53e5d-133">Na caixa de diálogo **procurar e selecionar um tipo .net** , em  **\<projeto atual >** , abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="53e5d-134">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-134">Click **OK**.</span></span> <span data-ttu-id="53e5d-135">Na caixa de diálogo **Editor de coleção de tipos** , clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="53e5d-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="53e5d-136">Selecione e exclua as atividades **ReceiveRequest** e **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="53e5d-137">Na caixa de ferramentas, arraste uma atividade **Buy_ReceiveAndSendReply** e **Checkout_Receive** para a atividade de **serviço sequencial** .</span><span class="sxs-lookup"><span data-stu-id="53e5d-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
