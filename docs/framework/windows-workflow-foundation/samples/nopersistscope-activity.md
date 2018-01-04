---
title: Atividade de NoPersistScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc651403988fa7558f79a4c99e42fb776efec4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="nopersistscope-activity"></a><span data-ttu-id="cafe4-102">Atividade de NoPersistScope</span><span class="sxs-lookup"><span data-stu-id="cafe4-102">NoPersistScope Activity</span></span>
<span data-ttu-id="cafe4-103">Este exemplo mostra como manipular um estado não-serializáveis e descartável em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cafe4-103">This sample shows how to manipulate a non-serializable and disposable state within a workflow.</span></span> <span data-ttu-id="cafe4-104">É importante que fluxos de trabalho não tentam manter o estado não-serializáveis e também é importante para objetos descartáveis ser limpado depois que são usados no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cafe4-104">It is important that workflows do not attempt to persist non-serializable state and it is also important for disposable objects to be cleaned up after they are used in workflow.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cafe4-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="cafe4-105">Demonstrates</span></span>  
 <span data-ttu-id="cafe4-106">atividade personalizado e designer de`NoPersistScope` .</span><span class="sxs-lookup"><span data-stu-id="cafe4-106">`NoPersistScope` custom activity and designer.</span></span>  
  
## <a name="using-the-nopersistzone-activity"></a><span data-ttu-id="cafe4-107">Usando a atividade de NoPersistZone</span><span class="sxs-lookup"><span data-stu-id="cafe4-107">Using the NoPersistZone activity</span></span>  
 <span data-ttu-id="cafe4-108">Quando o fluxo de trabalho de exemplo é executado, uma atividade personalizado chamada `CreateTextWriter` cria um objeto do tipo <xref:System.IO.TextWriter> e salvá-los em uma variável de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cafe4-108">When the sample workflow runs, a custom activity called `CreateTextWriter` creates an object of type <xref:System.IO.TextWriter> and saves it into a workflow variable.</span></span> <span data-ttu-id="cafe4-109"><xref:System.IO.TextWriter> é um objeto de <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="cafe4-109"><xref:System.IO.TextWriter> is an <xref:System.IDisposable> object.</span></span> <span data-ttu-id="cafe4-110">Este <xref:System.IO.TextWriter>, que é configurada para gravar em um arquivo denominado “out.txt” no diretório em que o exemplo reproduz, é usado por uma atividade de <xref:System.Activities.Statements.WriteLine> como ecoa qualquer texto que você digita no console.</span><span class="sxs-lookup"><span data-stu-id="cafe4-110">This <xref:System.IO.TextWriter>, which is configured to write to a file named ‘out.txt’ in the directory in which the sample runs, is used by a <xref:System.Activities.Statements.WriteLine> activity as it echoes any text you type in at the console.</span></span>  
  
 <span data-ttu-id="cafe4-111">A lógica de eco executam em uma atividade de `NoPersistScope` (o código para que também é a parte deste exemplo), que impede o fluxo de trabalho é mantido.</span><span class="sxs-lookup"><span data-stu-id="cafe4-111">The echo logic runs within a `NoPersistScope` activity (the code for which is also part of this sample), which prevents the workflow from being persisted.</span></span> <span data-ttu-id="cafe4-112">Se você digitar `unload` no console do, o host tenta manter a instância de fluxo de trabalho, mas esse tempo limite da operação porque o fluxo de trabalho permanece em um `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="cafe4-112">If you type in `unload` at the console, the host attempts to persist the workflow instance but this operation times out because the workflow remains within a `NoPersistScope`.</span></span> <span data-ttu-id="cafe4-113">O fluxo de trabalho também utiliza uma atividade personalizado chamada `Dispose` para descartar o objeto de <xref:System.IO.TextWriter> quando o fluxo de trabalho usando o terminar.</span><span class="sxs-lookup"><span data-stu-id="cafe4-113">The workflow also utilizes a custom activity called `Dispose` to dispose the <xref:System.IO.TextWriter> object when the workflow is finished using it.</span></span> <span data-ttu-id="cafe4-114">A atividade de `Dispose` é colocado dentro do bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> de atividade de <xref:System.Activities.Statements.TryCatch> em que a variável de <xref:System.IO.TextWriter> é declarado, para garantir que é executado se uma exceção deve ocorrer durante a execução do bloco try.</span><span class="sxs-lookup"><span data-stu-id="cafe4-114">The `Dispose` activity is placed within the <xref:System.Activities.Statements.TryCatch.Finally%2A> block of the <xref:System.Activities.Statements.TryCatch> activity in which the <xref:System.IO.TextWriter> variable is declared, to ensure that it runs even if an exception should occur during execution of the Try block.</span></span>  
  
 <span data-ttu-id="cafe4-115">Você pode digitar `exit` para concluir a instância de fluxo de trabalho e sair do programa.</span><span class="sxs-lookup"><span data-stu-id="cafe4-115">You can type in `exit` to complete the workflow instance and exit the program.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="cafe4-116">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="cafe4-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="cafe4-117">Abra a solução de NoPersistZone.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cafe4-117">Open the NoPersistZone.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cafe4-118">Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="cafe4-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="cafe4-119">Depois que a compilação foi bem-sucedida, pressione F5 ou selecione **iniciar depuração** do **depurar** menu como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** da **Depurar** menu para executar sem depuração.</span><span class="sxs-lookup"><span data-stu-id="cafe4-119">Once the build has succeeded, press F5 or select **Start Debugging** from the **Debug** menu alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="cafe4-120">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="cafe4-120">To cleanup (optional)</span></span>  
  
1.  <span data-ttu-id="cafe4-121">Para remover a instância Store SQL, Cleanup.cmd execução.</span><span class="sxs-lookup"><span data-stu-id="cafe4-121">To remove the SQL Instance Store, run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cafe4-122">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cafe4-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cafe4-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cafe4-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cafe4-124">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cafe4-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cafe4-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cafe4-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`