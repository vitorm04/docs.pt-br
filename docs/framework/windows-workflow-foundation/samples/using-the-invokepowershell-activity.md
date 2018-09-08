---
title: Usando a atividade de InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137727"
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="81af4-102">Usando a atividade de InvokePowerShell</span><span class="sxs-lookup"><span data-stu-id="81af4-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="81af4-103">O exemplo de InvokePowerShell demonstra como chamar comandos do Windows PowerShell que usam a atividade de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="81af4-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="81af4-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="81af4-105">Inovação simples de comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="81af4-106">Recuperar valores do canal de saída do Windows PowerShell e armazená-las em variáveis de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="81af4-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="81af4-107">Passar dados em janelas PowerShell como o pipeline de entrada para um comando executando.</span><span class="sxs-lookup"><span data-stu-id="81af4-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81af4-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81af4-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81af4-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="81af4-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81af4-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="81af4-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81af4-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="81af4-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="81af4-112">Discussão</span><span class="sxs-lookup"><span data-stu-id="81af4-112">Discussion</span></span>  
 <span data-ttu-id="81af4-113">Este exemplo contém os três projetos.</span><span class="sxs-lookup"><span data-stu-id="81af4-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="81af4-114">Nome do projeto</span><span class="sxs-lookup"><span data-stu-id="81af4-114">Project Name</span></span>|<span data-ttu-id="81af4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="81af4-115">Description</span></span>|<span data-ttu-id="81af4-116">Arquivos de chave</span><span class="sxs-lookup"><span data-stu-id="81af4-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="81af4-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="81af4-117">CodedClient</span></span>|<span data-ttu-id="81af4-118">Um aplicativo cliente de exemplo que use a atividade de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="81af4-119">-   **Program.CS**: cria programaticamente um fluxo de trabalho baseado sequência-que chama a atividade de InvokePowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="81af4-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="81af4-120">DesignerClient</span></span>|<span data-ttu-id="81af4-121">Um conjunto de atividades personalizados que contêm a atividade personalizado de `InvokePowerShell` e outras atividades personalizados diversos, e um fluxo de trabalho que os usa.</span><span class="sxs-lookup"><span data-stu-id="81af4-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="81af4-122">Atividades:</span><span class="sxs-lookup"><span data-stu-id="81af4-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="81af4-123">**{1&gt;printcollection.CS&lt;1**: uma atividade auxiliar que imprime todos os itens em uma coleção no console.</span><span class="sxs-lookup"><span data-stu-id="81af4-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="81af4-124">**{1&gt;ReadLine.CS&lt;1**: uma atividade auxiliar para ler a entrada do console.</span><span class="sxs-lookup"><span data-stu-id="81af4-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="81af4-125">O sistema de arquivos:</span><span class="sxs-lookup"><span data-stu-id="81af4-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="81af4-126">**{1&gt;Copy.XAML&lt;1**: uma atividade que copia um arquivo.</span><span class="sxs-lookup"><span data-stu-id="81af4-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="81af4-127">**{1&gt;CreateFile.XAML&lt;1**: uma atividade que cria um arquivo.</span><span class="sxs-lookup"><span data-stu-id="81af4-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="81af4-128">**{1&gt;DeleteFile.XAML&lt;1**: uma atividade que exclui um arquivo.</span><span class="sxs-lookup"><span data-stu-id="81af4-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="81af4-129">**{1&gt;makedir.XAML&lt;1**: uma atividade que cria um diretório.</span><span class="sxs-lookup"><span data-stu-id="81af4-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="81af4-130">**{1&gt;move.XAML&lt;1**: uma atividade que move um arquivo.</span><span class="sxs-lookup"><span data-stu-id="81af4-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="81af4-131">**{1&gt;ReadFile.XAML&lt;1**: uma atividade que lê um arquivo e retorna seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="81af4-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="81af4-132">**{1&gt;testpath.XAML&lt;1**: uma atividade que testa a existência de um caminho.</span><span class="sxs-lookup"><span data-stu-id="81af4-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="81af4-133">Processo:</span><span class="sxs-lookup"><span data-stu-id="81af4-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="81af4-134">**{1&gt;getprocess.XAML&lt;1**: uma atividade que obtém uma lista de processos em execução.</span><span class="sxs-lookup"><span data-stu-id="81af4-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="81af4-135">**{1&gt;stopprocess.XAML&lt;1**: uma atividade que impede que um processo específico.</span><span class="sxs-lookup"><span data-stu-id="81af4-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="81af4-136">**Program.CS**: chama o fluxo de trabalho Sequence1.</span><span class="sxs-lookup"><span data-stu-id="81af4-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="81af4-137">**Sequence1.XAML**: um fluxo de trabalho baseado sequência-.</span><span class="sxs-lookup"><span data-stu-id="81af4-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="81af4-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="81af4-138">PowerShell</span></span>|<span data-ttu-id="81af4-139">A atividade de `InvokePowerShell` e seus criadores associados.</span><span class="sxs-lookup"><span data-stu-id="81af4-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="81af4-140">Arquivos de atividade</span><span class="sxs-lookup"><span data-stu-id="81af4-140">Activity Files</span></span><br /><br /> <span data-ttu-id="81af4-141">-   **{1&gt;executepowershell.CS&lt;1**: A lógica principal de execução da atividade.</span><span class="sxs-lookup"><span data-stu-id="81af4-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="81af4-142">-   **{1&gt;invokepowershell.CS&lt;1**: O wrapper em torno de lógica de execução principal, que contém uma versão genérica (valor de retorno) e uma versão não genérica (valor de retorno não).</span><span class="sxs-lookup"><span data-stu-id="81af4-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="81af4-143">Esta é a interface pública para atividades.</span><span class="sxs-lookup"><span data-stu-id="81af4-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="81af4-144">-   **{1&gt;nopersistzone.CS&lt;1**: esta atividade impede que todas as atividades filhos persistam.</span><span class="sxs-lookup"><span data-stu-id="81af4-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="81af4-145">Essa classe é usada dentro da implementação de atividade de `InvokePowerShell` para impedir que a atividade é mid de- execução persistentes.</span><span class="sxs-lookup"><span data-stu-id="81af4-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="81af4-146">Arquivos de designer:</span><span class="sxs-lookup"><span data-stu-id="81af4-146">Designer files:</span></span><br /><br /> <span data-ttu-id="81af4-147">1.  **ArgumentDictionaryEditor.cs**: caixa de diálogo de um Windows que permite que o usuário edite os argumentos do `InvokePowerShell` atividade.</span><span class="sxs-lookup"><span data-stu-id="81af4-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="81af4-148">2.  **Genericinvokepowershelldesigner** e **2&gt;genericinvokepowershelldesigner.XAML.CS&lt;2**: define a aparência dos genéricos `InvokePowerShell` atividade no [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81af4-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="81af4-149">3.  **Invokepowershelldesigner** e **2&gt;invokepowershelldesigner.CS&lt;2**: define a aparência dos não genéricos `InvokePowerShell` atividade no [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81af4-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="81af4-150">Projetos de cliente são discutidos primeiro, pois é mais fácil compreender que a funcionalidade interna de atividade de PowerShell seu uso é compreendido uma vez.</span><span class="sxs-lookup"><span data-stu-id="81af4-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="81af4-151">Usando este exemplo</span><span class="sxs-lookup"><span data-stu-id="81af4-151">Using This Sample</span></span>  
 <span data-ttu-id="81af4-152">As seguintes seções descrevem como usar os três projetos no exemplo.</span><span class="sxs-lookup"><span data-stu-id="81af4-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="81af4-153">Usando o cliente codificado Projeto</span><span class="sxs-lookup"><span data-stu-id="81af4-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="81af4-154">O cliente de exemplo cria programaticamente uma atividade de sequência, que contém exemplos de vários métodos diferentes de usar a atividade de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="81af4-155">A primeira chamada inicia o Bloco De Notas.</span><span class="sxs-lookup"><span data-stu-id="81af4-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="81af4-156">A segunda chamada obter uma lista dos processos em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="81af4-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="81af4-157">`Output` é a variável usada para armazenar a saída do comando.</span><span class="sxs-lookup"><span data-stu-id="81af4-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="81af4-158">A chamada a seguir demonstra como reproduzir uma etapa de pré processamento em cada saída individuais de chamada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="81af4-159">`InitializationAction` é definido para a função essa saída uma representação de cadeia de caracteres para cada processo.</span><span class="sxs-lookup"><span data-stu-id="81af4-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="81af4-160">A coleção dessas cadeias de caracteres é retornada na variável de `Output` pela atividade de `InvokePowerShell<string>` .</span><span class="sxs-lookup"><span data-stu-id="81af4-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="81af4-161">Chamadas de sucesso de `InvokePowerShell` demonstram passar dados na atividade e obter saída e erros para fora.</span><span class="sxs-lookup"><span data-stu-id="81af4-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="81af4-162">Usando o cliente do Project designer</span><span class="sxs-lookup"><span data-stu-id="81af4-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="81af4-163">O projeto de DesignerClient consiste em um conjunto de atividades personalizados, quase que são compiladas que contêm a atividade de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="81af4-164">A maioria das atividades chamam a versão não genérico de atividade de `InvokePowerShell` , e não espera um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="81af4-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="81af4-165">Outras atividades usam a versão genérica de atividade de `InvokePowerShell` , e usam após o processo de argumento de `InitializationAction` os resultados.</span><span class="sxs-lookup"><span data-stu-id="81af4-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="81af4-166">Usando PowerShell Projeto</span><span class="sxs-lookup"><span data-stu-id="81af4-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="81af4-167">A ação principal da atividade ocorre na classe de `ExecutePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="81af4-168">Porque a execução de comandos de PowerShell não deve bloquear o segmento principal de fluxo de trabalho, a atividade é projetado para ser uma atividade assíncrono herança da classe de <xref:System.Activities.AsyncCodeActivity> .</span><span class="sxs-lookup"><span data-stu-id="81af4-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="81af4-169">O método de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> é chamado em tempo de execução de fluxo de trabalho para iniciar a execução da atividade.</span><span class="sxs-lookup"><span data-stu-id="81af4-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="81af4-170">Inicia chamando APIs de PowerShell para criar um pipeline de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="81af4-171">Então cria um comando de PowerShell e preenchê-los com parâmetros e variáveis.</span><span class="sxs-lookup"><span data-stu-id="81af4-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="81af4-172">Entradas corretamente em também são enviados ao pipeline no momento.</span><span class="sxs-lookup"><span data-stu-id="81af4-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="81af4-173">Finalmente, a pipeline é empacotada em um objeto de `PipelineInvokerAsyncResult` e retornada.</span><span class="sxs-lookup"><span data-stu-id="81af4-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="81af4-174">O objeto de `PipelineInvokerAsyncResult` registra um ouvinte e chama o pipeline.</span><span class="sxs-lookup"><span data-stu-id="81af4-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="81af4-175">Quando a execução for concluído, a saída e erros são armazenados no mesmo objeto de `PipelineInvokerAsyncResult` , e o controle é entregado de volta para o tempo de execução de fluxo de trabalho chamando o método de retorno originalmente passado <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="81af4-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="81af4-176">No final da execução do método, o tempo de execução de fluxo de trabalho chama o método de <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de atividade.</span><span class="sxs-lookup"><span data-stu-id="81af4-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="81af4-177">A classe de `InvokePowerShell` envolve a classe de `ExecutePowerShellCommand` e cria duas versões de atividade; uma versão genérica e não uma versão genérica.</span><span class="sxs-lookup"><span data-stu-id="81af4-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="81af4-178">A versão não genérico retorna a saída de execução de PowerShell diretamente, enquanto a versão genérica transforma os resultados individuais para o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="81af4-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="81af4-179">A versão genérica da atividade é implementada como um fluxo de trabalho sequencial que chama `ExecutePowerShellCommand` e posteriores processos seus resultados.</span><span class="sxs-lookup"><span data-stu-id="81af4-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="81af4-180">Para cada elemento na coleção de resultado, a etapa de pré processamento chama `InitializationAction` se é definida.</span><span class="sxs-lookup"><span data-stu-id="81af4-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="81af4-181">Se não, fazer uma conversão simples.</span><span class="sxs-lookup"><span data-stu-id="81af4-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="81af4-182">Para cada uma das duas atividades de `InvokePowerShell` (genéricos, e não genéricas), um designer foi criado.</span><span class="sxs-lookup"><span data-stu-id="81af4-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="81af4-183">InvokePowerShellDesigner.xaml e seu arquivo associado .cs definem a aparência em [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] para a versão não genérico de atividade de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="81af4-184">Dentro de InvokePowerShellDesigner.xaml, <xref:System.Windows.Controls.DockPanel> é usado para representar a interface gráfica.</span><span class="sxs-lookup"><span data-stu-id="81af4-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="81af4-185">Observe que a propriedade de `Text` da caixa de texto é uma associação bidirecional que garante que o valor da propriedade de `CommandText` da atividade é equivalente ao valor conectado no designer.</span><span class="sxs-lookup"><span data-stu-id="81af4-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="81af4-186">GenericInvokePowerShellDesigner.xaml e seu arquivo associado .cs definem a interface gráfica para atividades genérica de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="81af4-187">O designer é ligeiramente mais complicado porque ela permite que os usuários definir `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="81af4-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="81af4-188">O elemento chave é o uso de <xref:System.Activities.Presentation.WorkflowItemPresenter> para permitir ao arrastar e soltar de atividades filhos na superfície do designer de `InvokePowerShell` .</span><span class="sxs-lookup"><span data-stu-id="81af4-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="81af4-189">A personalização do designer não para com os arquivos .xaml que definem a aparência da atividade na tela de design.</span><span class="sxs-lookup"><span data-stu-id="81af4-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="81af4-190">As caixas de diálogo usadas para exibir os parâmetros da atividade também podem ser personalizadas.</span><span class="sxs-lookup"><span data-stu-id="81af4-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="81af4-191">Esses parâmetros e variáveis de PowerShell afetam o comportamento de comandos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81af4-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="81af4-192">A atividade os expõe como <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` tipos.</span><span class="sxs-lookup"><span data-stu-id="81af4-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="81af4-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml e PropertyEditorResources.cs definem a caixa de diálogo que permite que você edite esses tipos.</span><span class="sxs-lookup"><span data-stu-id="81af4-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81af4-194">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="81af4-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="81af4-195">Você deve instalar o Windows PowerShell para executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="81af4-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="81af4-196">Windows PowerShell pode ser instalado neste local: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="81af4-196">Windows PowerShell can be installed from this location: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="81af4-197">Para executar o cliente codificado</span><span class="sxs-lookup"><span data-stu-id="81af4-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="81af4-198">PowerShell.sln aberto usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81af4-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="81af4-199">Clique com o botão direito do mouse na solução e construa-a.</span><span class="sxs-lookup"><span data-stu-id="81af4-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="81af4-200">Clique com botão direito do **CodedClient** do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="81af4-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="81af4-201">Pressione CTRL+F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81af4-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="81af4-202">Para executar o cliente de designer</span><span class="sxs-lookup"><span data-stu-id="81af4-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="81af4-203">PowerShell.sln aberto usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81af4-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="81af4-204">Clique com o botão direito do mouse na solução e construa-a.</span><span class="sxs-lookup"><span data-stu-id="81af4-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="81af4-205">Clique com botão direito do **DesignerClient** do projeto e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="81af4-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="81af4-206">Pressione CTRL+F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81af4-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="81af4-207">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="81af4-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="81af4-208">Se fazer referência ao assembly ou projeto de atividade de `InvokePowerShell` de outro projeto resulta em um erro de compilação, você precisará adicionar manualmente o elemento de `<SpecificVersion>True</SpecificVersion>` o arquivo .csproj o novo projeto na linha que referencia `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="81af4-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="81af4-209">Se o Windows PowerShell não estiver instalado, a seguinte mensagem de erro é exibida no Visual Studio, assim que você adicionar um `InvokePowerShell` atividade em um fluxo de trabalho: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="81af4-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="81af4-210">No Windows 2.0, PowerShell programaticamente chamando `$input.MoveNext()` falha e scripts usando o produto de `$input.MoveNext()` erros não intencional e resultados.</span><span class="sxs-lookup"><span data-stu-id="81af4-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="81af4-211">Para resolver esse problema, considere usar o verbo `foreach` de PowerShell em vez de chamar `MoveNext()` para percorrer uma matriz.</span><span class="sxs-lookup"><span data-stu-id="81af4-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81af4-212">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81af4-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81af4-213">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="81af4-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81af4-214">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="81af4-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81af4-215">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="81af4-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`