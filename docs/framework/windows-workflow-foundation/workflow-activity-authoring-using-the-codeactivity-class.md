---
title: "Criação de atividade de fluxo de trabalho usando a classe de CodeActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2daec260c1224cd81280c6bf699b70efc2072588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="0b2b4-102">Criação de atividade de fluxo de trabalho usando a classe de CodeActivity</span><span class="sxs-lookup"><span data-stu-id="0b2b4-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="0b2b4-103">As atividades criadas por herança de <xref:System.Activities.CodeActivity> podem implementar o comportamento básico obrigatório substituindo o método de <xref:System.Activities.CodeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="0b2b4-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-codeactivitycontext"></a><span data-ttu-id="0b2b4-104">Usando CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="0b2b4-104">Using CodeActivityContext</span></span>  
 <span data-ttu-id="0b2b4-105">Recursos de tempo de execução de fluxo de trabalho podem ser acessados de dentro do método de <xref:System.Activities.CodeActivity.Execute%2A> usando membros de parâmetro de `context` , do tipo <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="0b2b4-106">Os recursos <xref:System.Activities.CodeActivityContext> direto disponível incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0b2b4-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="0b2b4-107">Definindo e obtendo os valores das variáveis e os argumentos.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-107">Getting and setting the values of variables and arguments.</span></span>  
  
-   <span data-ttu-id="0b2b4-108">Recursos personalizados de rastreamento que usam <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="0b2b4-109">Acesso às propriedades de execução da atividade usando <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="0b2b4-110">Para criar uma atividade personalizado que herda de CodeActivity</span><span class="sxs-lookup"><span data-stu-id="0b2b4-110">To create a custom activity that inherits from CodeActivity</span></span>  
  
1.  <span data-ttu-id="0b2b4-111">Abra[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b2b4-111">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0b2b4-112">Selecione **arquivo**, **novo**e, em seguida, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="0b2b4-113">Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="0b2b4-114">Selecione **biblioteca de atividades** no **modelos** janela.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="0b2b4-115">Nomeie o novo projeto HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-115">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="0b2b4-116">Activity1 no projeto HelloActivity e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="0b2b4-117">O projeto HelloActivity e selecione **adicionar** e, em seguida, **classe**.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="0b2b4-118">Nomeie a nova classe HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-118">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="0b2b4-119">No arquivo de HelloActivity.cs, adicione as seguintes diretivas de `using` .</span><span class="sxs-lookup"><span data-stu-id="0b2b4-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="0b2b4-120">Faça a nova classe herdar de <xref:System.Activities.CodeActivity> adicionando uma classe base para a declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  <span data-ttu-id="0b2b4-121">Adicionar funcionalidade à classe adicionando um método de <xref:System.Activities.CodeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="0b2b4-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="0b2b4-122">Use <xref:System.Activities.CodeActivityContext> para criar um registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0b2b4-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
