---
title: "Serviço da caixa de ferramentas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 294c530072b2d694f9aeb54d04b36d72bb6da637
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="toolbox-service"></a><span data-ttu-id="bd49c-102">Serviço da caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="bd49c-102">Toolbox Service</span></span>
<span data-ttu-id="bd49c-103">Este exemplo demonstra como atualizar as atividades da caixa de ferramentas de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com base no contexto de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bd49c-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="bd49c-104">O exemplo contém um fluxo de trabalho que modifica o conteúdo da caixa de ferramentas com base em se uma atividade personalizado está selecionada.</span><span class="sxs-lookup"><span data-stu-id="bd49c-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bd49c-105">Discussão</span><span class="sxs-lookup"><span data-stu-id="bd49c-105">Discussion</span></span>  
 <span data-ttu-id="bd49c-106">Durante a criação de fluxo de trabalho, os clientes desejam geralmente a caixa de ferramentas para ser contextuais.</span><span class="sxs-lookup"><span data-stu-id="bd49c-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="bd49c-107">Por exemplo, o usuário pode querer para garantir que a caixa de ferramentas mostra algumas atividades adicionais quando uma atividade específica é adicionada ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bd49c-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="bd49c-108">Se as atividades são removidas de fluxo de trabalho, a caixa de ferramentas deve reagir adequadamente com base nos requisitos do domínio.</span><span class="sxs-lookup"><span data-stu-id="bd49c-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="bd49c-109">Em um designer novamente hospedado de fluxo de trabalho, você controla o controle de caixa de ferramentas e pode garantir que com base nas alterações no modelo fluxo de trabalho, o host que os disparadores exibe alterações no controle de caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="bd49c-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="bd49c-110">No entanto, em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], a caixa de ferramentas não é controlada pelo usuário e uma interface é necessária para modificar seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bd49c-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="bd49c-111">`IActivityToolboxService` é a interface.</span><span class="sxs-lookup"><span data-stu-id="bd49c-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="bd49c-112">API fornece os quatro métodos.</span><span class="sxs-lookup"><span data-stu-id="bd49c-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd49c-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bd49c-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd49c-114">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WorkflowSimulator.sln.</span><span class="sxs-lookup"><span data-stu-id="bd49c-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="bd49c-115">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="bd49c-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="bd49c-116">Abra o arquivo de Workflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="bd49c-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="bd49c-117">Adicionar um **CustomActivity** arrastando e soltando-o na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="bd49c-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="bd49c-118">Observe que a chamada de uma categoria de caixa de ferramentas adicional: **nova categoria de WF** com uma atividade adicional **atribuir**.</span><span class="sxs-lookup"><span data-stu-id="bd49c-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="bd49c-119">Desmarque agora o **CustomActivity** arrastando outra atividade nela.</span><span class="sxs-lookup"><span data-stu-id="bd49c-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="bd49c-120">O item **atribuir** na categoria **nova categoria de WF** na caixa de ferramentas é removido.</span><span class="sxs-lookup"><span data-stu-id="bd49c-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="bd49c-121">Além disso, porque não há mais item deixado na categoria, a categoria é removida também.</span><span class="sxs-lookup"><span data-stu-id="bd49c-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="bd49c-122">Selecione o **CustomActivity** novamente e a categoria e **atribuir** atividade é adicionada novamente.</span><span class="sxs-lookup"><span data-stu-id="bd49c-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd49c-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bd49c-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd49c-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bd49c-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bd49c-125">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bd49c-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd49c-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bd49c-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
