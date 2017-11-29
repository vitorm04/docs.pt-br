---
title: "Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a811609f601e844d55d4173eb94df24701fcc7d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="7c54c-102">Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="7c54c-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="7c54c-103">O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] apresenta uma melhor integração entre serviços Web e fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="7c54c-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="7c54c-104">A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro.</span><span class="sxs-lookup"><span data-stu-id="7c54c-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="7c54c-105">A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato.</span><span class="sxs-lookup"><span data-stu-id="7c54c-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c54c-106">Este tópico fornece orientação passo a passo sobre como criar um serviço de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="7c54c-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="7c54c-107">desenvolvimento de serviço de fluxo de trabalho do contrato, primeiro, consulte [desenvolvimento de serviço de fluxo de trabalho primeiro contrato](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="7c54c-107"> contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="7c54c-108">Criando o projeto de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7c54c-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="7c54c-109">Em [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], selecione **arquivo**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-109">In [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], select **File**, **New Project**.</span></span> <span data-ttu-id="7c54c-110">Selecione o **WCF** nó sob o **c#** nó o **modelos** de árvore e selecione o **aplicativo de serviço de fluxo de trabalho WCF** modelo.</span><span class="sxs-lookup"><span data-stu-id="7c54c-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="7c54c-111">Nomeie o novo projeto `ContractFirst` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="7c54c-112">Criando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7c54c-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="7c54c-113">Clique com botão direito no projeto no **Solution Explorer** e selecione **adicionar**, **Novo Item...** .</span><span class="sxs-lookup"><span data-stu-id="7c54c-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="7c54c-114">Selecione o **código** nó à esquerda e o **classe** modelo à direita.</span><span class="sxs-lookup"><span data-stu-id="7c54c-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="7c54c-115">Nomeie a nova classe `IBookService` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="7c54c-116">Na parte superior da janela de código que aparece, adicione uma instrução Using a `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="7c54c-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="7c54c-117">Altere a definição de classe de exemplo à seguinte definição da interface.</span><span class="sxs-lookup"><span data-stu-id="7c54c-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4.  <span data-ttu-id="7c54c-118">Compilar o projeto, pressionando **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="7c54c-119">Importando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7c54c-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="7c54c-120">Clique com botão direito no projeto no **Solution Explorer** e selecione **contrato de serviço de importação**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="7c54c-121">Em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="7c54c-122">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="7c54c-123">Uma caixa de diálogo abrirá, alertando-o de que a operação foi concluída com êxito e que as atividades geradas serão exibidas na caixa de ferramentas depois que você compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="7c54c-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="7c54c-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="7c54c-125">Compilar o projeto, pressionando **Ctrl + Shift + B**, de modo que as atividades importadas serão exibido na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7c54c-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="7c54c-126">Em **Solution Explorer**, abra Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="7c54c-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="7c54c-127">O serviço de fluxo de trabalho aparecerá no designer.</span><span class="sxs-lookup"><span data-stu-id="7c54c-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="7c54c-128">Selecione o **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="7c54c-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="7c54c-129">Na janela Propriedades, clique o **...**</span><span class="sxs-lookup"><span data-stu-id="7c54c-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="7c54c-130">no botão de **ImplementedContract** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c54c-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="7c54c-131">No **Editor de coleção do tipo** janela que aparece, clique no **tipo** suspenso e selecione o **procurar tipos...**</span><span class="sxs-lookup"><span data-stu-id="7c54c-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="7c54c-132">entrada.</span><span class="sxs-lookup"><span data-stu-id="7c54c-132">entry.</span></span> <span data-ttu-id="7c54c-133">No **procurar e selecione um .net tipo** caixa de diálogo, em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="7c54c-134">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-134">Click **OK**.</span></span> <span data-ttu-id="7c54c-135">No **Editor de coleção do tipo** caixa de diálogo, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7c54c-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="7c54c-136">Selecione e exclua o **ReceiveRequest** e **SendResponse** atividades.</span><span class="sxs-lookup"><span data-stu-id="7c54c-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="7c54c-137">Na caixa de ferramentas, arraste um **Buy_ReceiveAndSendReply** e um **Checkout_Receive** atividade para o **serviço sequencial** atividade.</span><span class="sxs-lookup"><span data-stu-id="7c54c-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
