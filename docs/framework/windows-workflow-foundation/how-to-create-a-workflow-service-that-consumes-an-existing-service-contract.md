---
title: 'Como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 06d4d4f6687979f4fd54e919ca6f236a5b5402e8
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843002"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="b7a27-102">Como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente</span><span class="sxs-lookup"><span data-stu-id="b7a27-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="b7a27-103">O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] apresenta uma melhor integração entre serviços Web e fluxos de trabalho na forma de desenvolvimento de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="b7a27-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="b7a27-104">A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que você crie o contrato no código primeiro.</span><span class="sxs-lookup"><span data-stu-id="b7a27-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="b7a27-105">A ferramenta em seguida gera automaticamente um modelo de atividade na caixa de ferramentas para as operações no contrato.</span><span class="sxs-lookup"><span data-stu-id="b7a27-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7a27-106">Este tópico fornece orientação passo a passo sobre como criar um serviço de fluxo de trabalho de primeiro contrato.</span><span class="sxs-lookup"><span data-stu-id="b7a27-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="b7a27-107">Para obter mais informações sobre o desenvolvimento de serviço de fluxo de trabalho de primeiro contrato, consulte [desenvolvimento de serviço de fluxo de trabalho de primeiro contrato](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="b7a27-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="b7a27-108">Criando o projeto de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b7a27-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="b7a27-109">No Visual Studio, selecione **arquivo**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="b7a27-110">Selecione o **WCF** nó sob o **C#** nó no **modelos** de árvore e, em seguida, selecione o **aplicativo de serviço de fluxo de trabalho WCF** modelo.</span><span class="sxs-lookup"><span data-stu-id="b7a27-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="b7a27-111">Nomeie o novo projeto `ContractFirst` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="b7a27-112">Criando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="b7a27-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="b7a27-113">Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **Add**, **Novo Item...** .</span><span class="sxs-lookup"><span data-stu-id="b7a27-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="b7a27-114">Selecione o **código** nó à esquerda e o **classe** modelo à direita.</span><span class="sxs-lookup"><span data-stu-id="b7a27-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="b7a27-115">Nomeie a nova classe `IBookService` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="b7a27-116">Na parte superior da janela de código que aparece, adicione uma instrução Using a `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="b7a27-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="b7a27-117">Altere a definição de classe de exemplo à seguinte definição da interface.</span><span class="sxs-lookup"><span data-stu-id="b7a27-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4.  <span data-ttu-id="b7a27-118">Compile o projeto pressionando **Ctrl + Shift + B**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="b7a27-119">Importando o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="b7a27-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="b7a27-120">Clique com botão direito no projeto no **Gerenciador de soluções** e selecione **contrato de serviço de importação**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="b7a27-121">Sob  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="b7a27-122">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="b7a27-123">Uma caixa de diálogo abrirá, alertando-o de que a operação foi concluída com êxito e que as atividades geradas serão exibidas na caixa de ferramentas depois que você compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="b7a27-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="b7a27-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="b7a27-125">Compile o projeto pressionando **Ctrl + Shift + B**, de modo que as atividades importadas aparecerão na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="b7a27-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="b7a27-126">Na **Gerenciador de soluções**, abra Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="b7a27-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="b7a27-127">O serviço de fluxo de trabalho aparecerá no designer.</span><span class="sxs-lookup"><span data-stu-id="b7a27-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="b7a27-128">Selecione o **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="b7a27-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="b7a27-129">Na janela Propriedades, clique o **...**</span><span class="sxs-lookup"><span data-stu-id="b7a27-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="b7a27-130">botão de **ImplementedContract** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b7a27-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="b7a27-131">No **Editor de coleção do tipo** janela que aparece, clique no **tipo** lista suspensa e selecione o **procurar tipos...**</span><span class="sxs-lookup"><span data-stu-id="b7a27-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="b7a27-132">entrada.</span><span class="sxs-lookup"><span data-stu-id="b7a27-132">entry.</span></span> <span data-ttu-id="b7a27-133">No **navegue e selecione um tipo .NET** caixa de diálogo, em  **\<projeto atual >**, abra todos os subnós e selecione **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="b7a27-134">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-134">Click **OK**.</span></span> <span data-ttu-id="b7a27-135">No **Editor de coleção do tipo** caixa de diálogo, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b7a27-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="b7a27-136">Selecione e exclua as **ReceiveRequest** e **SendResponse** atividades.</span><span class="sxs-lookup"><span data-stu-id="b7a27-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="b7a27-137">Na caixa de ferramentas, arraste um **Buy_ReceiveAndSendReply** e uma **Checkout_Receive** atividade para o **Sequential Service** atividade.</span><span class="sxs-lookup"><span data-stu-id="b7a27-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
