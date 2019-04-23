---
title: Usando extensões de atividade
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768950"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="90adb-102">Usando extensões de atividade</span><span class="sxs-lookup"><span data-stu-id="90adb-102">Using Activity Extensions</span></span>
<span data-ttu-id="90adb-103">As atividades podem interagir com as extensões do aplicativo de fluxo de trabalho que permitem que o host fornece funcionalidade adicional que não é modelada explicitamente no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="90adb-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="90adb-104">Este tópico descreve como criar e usar uma extensão para contar o número de vezes que a atividade é executado.</span><span class="sxs-lookup"><span data-stu-id="90adb-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="90adb-105">Para usar uma extensão de atividade para contar executa</span><span class="sxs-lookup"><span data-stu-id="90adb-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="90adb-106">Abra o Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="90adb-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="90adb-107">Selecione **novos**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="90adb-107">Select **New**, **Project**.</span></span> <span data-ttu-id="90adb-108">Sob o **Visual c#** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="90adb-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="90adb-109">Selecione **aplicativo de Console do fluxo de trabalho** da lista de modelos.</span><span class="sxs-lookup"><span data-stu-id="90adb-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="90adb-110">Nomeie o projeto `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="90adb-110">Name the project `Extensions`.</span></span> <span data-ttu-id="90adb-111">Clique em **OK** para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="90adb-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="90adb-112">Adicionar um `using` instrução no arquivo Program.cs para o **Collections** namespace.</span><span class="sxs-lookup"><span data-stu-id="90adb-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="90adb-113">No arquivo Program.cs, crie uma nova classe chamada **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="90adb-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="90adb-114">O código a seguir cria uma extensão de fluxo de trabalho que controla IDs de instância quando seu **registrar** método é chamado.</span><span class="sxs-lookup"><span data-stu-id="90adb-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="90adb-115">Criar uma atividade que consome os **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="90adb-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="90adb-116">O código a seguir define uma atividade que recupera o **ExecutionCountExtension** objeto de tempo de execução e chama seu **registrar** método quando a atividade é executada.</span><span class="sxs-lookup"><span data-stu-id="90adb-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="90adb-117">Implementar a atividade na **Main** método do arquivo program.cs.</span><span class="sxs-lookup"><span data-stu-id="90adb-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="90adb-118">O código a seguir contém métodos para gerar dois fluxos de trabalho diferentes, para executar cada fluxo de trabalho várias vezes, e exibir os dados resultante que estão contidos na extensão.</span><span class="sxs-lookup"><span data-stu-id="90adb-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
