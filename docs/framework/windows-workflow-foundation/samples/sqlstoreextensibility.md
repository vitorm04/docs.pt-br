---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3e63a11ce87c95a5afc8e7f60c8e262da5c6bd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="sqlstoreextensibility"></a><span data-ttu-id="52396-102">SQLStoreExtensibility</span><span class="sxs-lookup"><span data-stu-id="52396-102">SQLStoreExtensibility</span></span>
<span data-ttu-id="52396-103">Este exemplo demonstra o uso e configuração de propriedades elevadas no armazenamento de instância de fluxo de trabalho SQL.</span><span class="sxs-lookup"><span data-stu-id="52396-103">This sample demonstrates the use and configuration of promoted properties in the SQL workflow instance store.</span></span> <span data-ttu-id="52396-104">O armazenamento de instância de fluxo de trabalho do SQL é uma implementação SQL- base de um armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="52396-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="52396-105">Permite que uma instância salve o estado e carrega o estado para e de um base de dados SQL Server ou do SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="52396-105">It allows an instance to save its state and load its state to and from a SQL Server or SQL Server Express database.</span></span> <span data-ttu-id="52396-106">O recurso de extensibilidade de armazenamento permite que o usuário defina as propriedades que são armazenadas no armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="52396-106">The store extensibility feature allows the user to define properties that are stored in the instance store.</span></span> <span data-ttu-id="52396-107">Essas propriedades são exibidas em uma exibição promovida propriedades que permite que o usuário possa ver para eles.</span><span class="sxs-lookup"><span data-stu-id="52396-107">These properties are displayed in a promoted properties view that allows the user to query for them.</span></span>  
  
 <span data-ttu-id="52396-108">Esse exemplo consiste em um fluxo de trabalho que implementa um serviço de contagem.</span><span class="sxs-lookup"><span data-stu-id="52396-108">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="52396-109">Uma vez que o método inicial do serviço é chamado, o serviço conta 0 a 29.</span><span class="sxs-lookup"><span data-stu-id="52396-109">Once the service's start method is invoked, the service counts from 0 to 29.</span></span> <span data-ttu-id="52396-110">O contador é incrementado uma vez a cada 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="52396-110">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="52396-111">Após cada contagem, o fluxo de trabalho persiste.</span><span class="sxs-lookup"><span data-stu-id="52396-111">After each count, the workflow persists.</span></span> <span data-ttu-id="52396-112">O valor do contador atual é armazenado no armazenamento de instância como uma propriedade promovida.</span><span class="sxs-lookup"><span data-stu-id="52396-112">The current counter value is stored in the instance store as a promoted property.</span></span>  
  
 <span data-ttu-id="52396-113">O fluxo de trabalho de contagem dica é hospedado por um host de Serviço de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="52396-113">The Counting Workflow is self-hosted by a Workflow Service Host.</span></span> <span data-ttu-id="52396-114">O método de `Main` do programa executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="52396-114">The program's `Main` method performs the following actions:</span></span>  
  
-   <span data-ttu-id="52396-115">Cria uma instância de host de Serviço de Fluxo de Trabalho que hospeda o fluxo de trabalho de contagem e define os pontos de extremidade em que o fluxo de trabalho de contagem pode ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="52396-115">Creates an instance of the Workflow Service Host that hosts the Counting Workflow and defines the endpoints under which the Counting Workflow can be reached.</span></span>  
  
-   <span data-ttu-id="52396-116">Define um comportamento do armazenamento de instância de fluxo de trabalho SQL, que é usado para configurar o armazenamento de instância de fluxo de trabalho SQL.</span><span class="sxs-lookup"><span data-stu-id="52396-116">Defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="52396-117">O armazenamento é instruído para manipular `CountStatus` como uma propriedade promovida.</span><span class="sxs-lookup"><span data-stu-id="52396-117">The store is instructed to treat `CountStatus` as a promoted property.</span></span>  
  
-   <span data-ttu-id="52396-118">Cria um cliente que chama o método inicial do fluxo de trabalho de contagem.</span><span class="sxs-lookup"><span data-stu-id="52396-118">Creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="52396-119">O programa é iniciado uma vez, o contador inicia automaticamente a contagem.</span><span class="sxs-lookup"><span data-stu-id="52396-119">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="52396-120">Observe que pode levar alguns segundos para carregar a instância e configurar o armazenamento de instância de fluxo de trabalho SQL.</span><span class="sxs-lookup"><span data-stu-id="52396-120">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span>  
  
 <span data-ttu-id="52396-121">Para elevar o valor do contador como uma propriedade personalizada, as seguintes etapas devem ser executadas:</span><span class="sxs-lookup"><span data-stu-id="52396-121">To promote the counter value as a custom property, the following steps must be taken:</span></span>  
  
1.  <span data-ttu-id="52396-122">A classe `CounterStatus` define uma extensão da instância do tipo <xref:System.Activities.Persistence.PersistenceParticipant>, que é usado por atividades para fornecer variáveis de estado.</span><span class="sxs-lookup"><span data-stu-id="52396-122">The class `CounterStatus` defines an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span> <span data-ttu-id="52396-123">`Count` é definido como um valor somente gravação.</span><span class="sxs-lookup"><span data-stu-id="52396-123">`Count` is defined as a write-only value.</span></span> <span data-ttu-id="52396-124">Quando uma instância de fluxo de trabalho chega a um ponto de persistência, a extensão de instância salva a propriedade de `Count` na coleção de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="52396-124">When a workflow instance comes to a persistence point, the instance extension saves the `Count` property into the persistence data collection.</span></span>  
  
2.  <span data-ttu-id="52396-125">Ao criar o armazenamento de instância, uma nova propriedade, `CountStatus`, é definida com o método de `store.Promote()` .</span><span class="sxs-lookup"><span data-stu-id="52396-125">When creating the instance store, a new property, `CountStatus`, is defined through the `store.Promote()` method.</span></span>  
  
3.  <span data-ttu-id="52396-126">A atividade de `SaveCounter` de fluxo de trabalho atribui o valor do contador atual para o campo status de `Count` .</span><span class="sxs-lookup"><span data-stu-id="52396-126">The workflow's `SaveCounter` activity assigns the current counter value to the `Count` status field.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="52396-127">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="52396-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="52396-128">Crie o base de dados da instância.</span><span class="sxs-lookup"><span data-stu-id="52396-128">Create the instance store database.</span></span>  
  
    1.  <span data-ttu-id="52396-129">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52396-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="52396-130">Navegue para o diretório de exemplo (\ \ WF básico persistência SqlStoreExtensibility \ \ \ CS) e a CreateInstanceStore.cmd executado no prompt de comando de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="52396-130">Navigate to the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility\CS) and run CreateInstanceStore.cmd in the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="52396-131">O script de CreateInstanceStore.cmd tentar criar o base de dados na instância padrão do SQL Server 2008 Express.</span><span class="sxs-lookup"><span data-stu-id="52396-131">The CreateInstanceStore.cmd script attempts to create the database on the default instance of SQL Server 2008 Express.</span></span> <span data-ttu-id="52396-132">Se você deseja instalar o base de dados em uma instância diferente, modifique o script para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="52396-132">If you want to install the database on a different instance, modify the script to do so.</span></span>  
  
2.  <span data-ttu-id="52396-133">Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e carregar a solução de SqlStoreExtensibility.sln e construa-a pressionando CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="52396-133">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and load the SqlStoreExtensibility.sln solution and build it by pressing CTRL+SHIFT+B.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="52396-134">Se você instalou o base de dados em uma instância não padrão do SQL Server, atualizar a cadeia de conexão no código antes de criar a solução.</span><span class="sxs-lookup"><span data-stu-id="52396-134">If you installed the database on a non-default instance of SQL Server, update the connection string in the code prior to building the solution.</span></span>  
  
3.  <span data-ttu-id="52396-135">Executar o exemplo com privilégios de administrador, navegue até o diretório do projeto bin (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) em [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], clicando duas vezes SqlStoreExtensibility.exe e selecionando **executar como Administrador**.</span><span class="sxs-lookup"><span data-stu-id="52396-135">Run the sample with administrator privileges by navigating to the project’s bin directory (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], right-clicking SqlStoreExtensibility.exe and selecting **Run as Administrator**.</span></span>  
  
### <a name="to-verify-the-sample-is-working-correctly"></a><span data-ttu-id="52396-136">Para verificar o exemplo está funcionando corretamente</span><span class="sxs-lookup"><span data-stu-id="52396-136">To verify the sample is working correctly</span></span>  
  
1.  <span data-ttu-id="52396-137">Use o SQL Server Management Studio para exibir o conteúdo da tabela de instância selecionando **bancos de dados**, **InstanceStore**e, em seguida,  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** no Pesquisador de objetos, clique com botão direito **System.ServiceModel.Activities.DurableInstancing.InstanceTable** e selecione  **Selecione os primeiros 1.000 linhas**.</span><span class="sxs-lookup"><span data-stu-id="52396-137">Use SQL Server Management Studio to view the contents of the instance table by selecting **Databases**, **InstanceStore**, and then **System.ServiceModel.Activities.DurableInstancing.InstanceTable** in the Object Explorer, right-click **System.ServiceModel.Activities.DurableInstancing.InstanceTable** and select **Select Top 1000 Rows**.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="52396-138">SQL Server Management Studio, consulte [apresentando o SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span><span class="sxs-lookup"><span data-stu-id="52396-138"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)</span></span>  
  
2.  <span data-ttu-id="52396-139">Observe as instâncias de fluxo de trabalho listadas.</span><span class="sxs-lookup"><span data-stu-id="52396-139">Observe the workflow instances listed.</span></span>  
  
3.  <span data-ttu-id="52396-140">Em um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , execute o script de QueryInstanceStore.cmd localizado no diretório de exemplo (\ \ WF básico \ \ SqlStoreExtensibility persistência).</span><span class="sxs-lookup"><span data-stu-id="52396-140">In a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run the QueryInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
4.  <span data-ttu-id="52396-141">Observe o valor do contador exibido em **CountStatus**.</span><span class="sxs-lookup"><span data-stu-id="52396-141">Observe the counter value displayed under **CountStatus**.</span></span>  
  
5.  <span data-ttu-id="52396-142">Execute o script algumas vezes para ver o **CountStats** alteração de valor.</span><span class="sxs-lookup"><span data-stu-id="52396-142">Run the script a few times to see the **CountStats** value change.</span></span>  
  
6.  <span data-ttu-id="52396-143">Pressione ENTER para encerrar o aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="52396-143">Press ENTER to terminate the workflow application.</span></span>  
  
### <a name="to-uninstall-the-sample"></a><span data-ttu-id="52396-144">Para desinstalar o exemplo</span><span class="sxs-lookup"><span data-stu-id="52396-144">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="52396-145">Remova a base de dados da instância executando o script de RemoveInstanceStore.cmd localizado no diretório de exemplo (\ \ WF básico \ \ SqlStoreExtensibility persistência).</span><span class="sxs-lookup"><span data-stu-id="52396-145">Remove the instance store database by running the RemoveInstanceStore.cmd script located in the sample directory (\WF\Basic\Persistence\SqlStoreExtensibility).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52396-146">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="52396-146">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52396-147">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="52396-147">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52396-148">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="52396-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52396-149">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="52396-149">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a><span data-ttu-id="52396-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52396-150">See Also</span></span>  
 [<span data-ttu-id="52396-151">Persistência de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="52396-151">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="52396-152">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="52396-152">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="52396-153">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="52396-153">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
