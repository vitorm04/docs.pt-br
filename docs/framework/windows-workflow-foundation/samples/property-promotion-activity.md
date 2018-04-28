---
title: Atividade da promoção de propriedade
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12f7aa4bd10a22a3cd3ea361e32016b95e41e46b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="property-promotion-activity"></a><span data-ttu-id="05c9a-102">Atividade da promoção de propriedade</span><span class="sxs-lookup"><span data-stu-id="05c9a-102">Property Promotion Activity</span></span>
<span data-ttu-id="05c9a-103">Este exemplo fornece uma solução ponta a ponta que integre o recurso de promoção de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> diretamente na experiência de criação de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="05c9a-104">Uma coleção de elementos de configuração, as atividades de fluxo de trabalho, e as extensões de fluxo de trabalho que simplificam o uso de recurso da promoção são fornecidas.</span><span class="sxs-lookup"><span data-stu-id="05c9a-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="05c9a-105">Além disso, o exemplo contém um fluxo de trabalho simples que demonstra como usar essa coleção.</span><span class="sxs-lookup"><span data-stu-id="05c9a-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c9a-106">Exemplos são fornecidos para fins educacionais somente.</span><span class="sxs-lookup"><span data-stu-id="05c9a-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="05c9a-107">Não são destinados para um ambiente de produção, e não foram testados em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="05c9a-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="05c9a-108">Microsoft não fornece suporte técnico para esses exemplos.</span><span class="sxs-lookup"><span data-stu-id="05c9a-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="05c9a-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="05c9a-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="05c9a-110">Um base de dados inicializado de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="05c9a-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="05c9a-111">Projetos de exemplo</span><span class="sxs-lookup"><span data-stu-id="05c9a-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="05c9a-112">O **PropertyPromotionActivity** projeto contém arquivos pertencentes a elementos de configuração específicas de promoção, atividades de fluxo de trabalho e extensões de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="05c9a-113">O **CounterServiceApplication** projeto contém um fluxo de trabalho de exemplo que usa o **SqlWorkflowInstanceStorePromotion** projeto.</span><span class="sxs-lookup"><span data-stu-id="05c9a-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="05c9a-114">Um script SQL (PropertyPromotionActivitySQLSample.sql) que deve ser executado com o base de dados de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .</span><span class="sxs-lookup"><span data-stu-id="05c9a-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="05c9a-115">Um arquivo de solução que vincula os dois projetos de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="05c9a-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="05c9a-116">Para configurar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="05c9a-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="05c9a-117">Inicializar uma base de dados de persistência de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="05c9a-118">Navegue para o diretório de exemplo (\ \ WF básico \ \ PropertyPromotionActivity persistência) e a CreateInstanceStore.cmd executado.</span><span class="sxs-lookup"><span data-stu-id="05c9a-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="05c9a-119">Se os privilégios de administrador não estão disponíveis, crie um login SQL Server.</span><span class="sxs-lookup"><span data-stu-id="05c9a-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="05c9a-120">No SQL Server Management Studio, vá para **segurança**, **logons**.</span><span class="sxs-lookup"><span data-stu-id="05c9a-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="05c9a-121">Clique com botão direito **logons** e crie um novo logon.</span><span class="sxs-lookup"><span data-stu-id="05c9a-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="05c9a-122">Adicionar o usuário ACL para a função SQL abrindo **bancos de dados**, **InstanceStore**, **segurança**.</span><span class="sxs-lookup"><span data-stu-id="05c9a-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="05c9a-123">Clique com botão direito **usuários** e selecione **novo usuário**.</span><span class="sxs-lookup"><span data-stu-id="05c9a-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="05c9a-124">Definir o **nome de logon** para o usuário criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="05c9a-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="05c9a-125">Adicione o usuário à função de associação System.Activities.DurableInstancing.InstanceStoreUsers (e outros) de base de dados.</span><span class="sxs-lookup"><span data-stu-id="05c9a-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="05c9a-126">Observe que o usuário pode existir ainda (por exemplo, dbo de usuário).</span><span class="sxs-lookup"><span data-stu-id="05c9a-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="05c9a-127">Abra o arquivo de solução de PropertyPromotionActivity.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05c9a-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="05c9a-128">Se você criou o armazenamento de instância em uma base de dados que não seja uma instalação local do SQL Server Express edition, você deve atualizar a cadeia de conexão caracteres de base de dados.</span><span class="sxs-lookup"><span data-stu-id="05c9a-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="05c9a-129">Alterar o arquivo App. config sob o **CounterServiceApplication** definindo o valor da `connectionString` atributo no `sqlWorkflowInstanceStorePromotion` nó para que ele aponte para o banco de dados de persistência que foi inicializado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="05c9a-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="05c9a-130">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="05c9a-130">Build and run the solution.</span></span> <span data-ttu-id="05c9a-131">Isso enfiará o serviço do contador WF e iniciará automaticamente uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="05c9a-132">Selecione rapidamente todas as linhas em dbo []. O modo de CounterService [] em seu base de dados de persistência (esta exibição foi adicionada executando CreateInstanceStore.cmd na etapa 1).</span><span class="sxs-lookup"><span data-stu-id="05c9a-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="05c9a-133">Você verá um conjunto de resultados semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="05c9a-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="05c9a-134">InstanceId</span><span class="sxs-lookup"><span data-stu-id="05c9a-134">InstanceId</span></span>|<span data-ttu-id="05c9a-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="05c9a-135">CounterValue</span></span>|<span data-ttu-id="05c9a-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="05c9a-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="05c9a-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="05c9a-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="05c9a-138">12</span><span class="sxs-lookup"><span data-stu-id="05c9a-138">12</span></span>|<span data-ttu-id="05c9a-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="05c9a-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="05c9a-140">Porque você mantiver atualizar a exibição, você observará que o CounterValue e CounterValueLastUpdated alteram cada dois segundos.</span><span class="sxs-lookup"><span data-stu-id="05c9a-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="05c9a-141">Este é o intervalo em que o contador se atualiza.</span><span class="sxs-lookup"><span data-stu-id="05c9a-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="05c9a-142">O CounterValue e CounterValueLastUpdated representam propriedades elevadas para esse fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="05c9a-143">Para remover o exemplo</span><span class="sxs-lookup"><span data-stu-id="05c9a-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="05c9a-144">Execução RemoveInstanceStore.cmd no diretório de exemplo (\ \ WF básico \ \ PropertyPromotionActivity persistência).</span><span class="sxs-lookup"><span data-stu-id="05c9a-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="05c9a-145">Entender este exemplo</span><span class="sxs-lookup"><span data-stu-id="05c9a-145">Understanding This Sample</span></span>  
 <span data-ttu-id="05c9a-146">O exemplo contém dois projetos e um arquivo SQL:</span><span class="sxs-lookup"><span data-stu-id="05c9a-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="05c9a-147">**CounterServiceApplication** é um aplicativo de console que hospeda um serviço simples do WF do contador.</span><span class="sxs-lookup"><span data-stu-id="05c9a-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="05c9a-148">Em cima de receber uma mensagem unidirecional através do ponto final de `Start` , o fluxo de trabalho conta 0 a 29, incremento uma variável de contagem cada dois segundos.</span><span class="sxs-lookup"><span data-stu-id="05c9a-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="05c9a-149">Após cada incremento disso, o fluxo de trabalho persistir, e as propriedades elevadas são atualizados no dbo []. O modo de CounterService [].</span><span class="sxs-lookup"><span data-stu-id="05c9a-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="05c9a-150">Quando o aplicativo de console é executado, hospeda o serviço de WF e envia uma mensagem ao ponto final de `Start` , criando uma instância do contador WF.</span><span class="sxs-lookup"><span data-stu-id="05c9a-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="05c9a-151">**PropertyPromotionActivity** é uma biblioteca de classe que contém os elementos de configuração, as atividades de fluxo de trabalho e extensões de fluxo de trabalho que o **CounterServiceApplication** usa.</span><span class="sxs-lookup"><span data-stu-id="05c9a-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="05c9a-152">**PropertyPromotionActivitySQLSample.sql** cria e adiciona o modo de exibição [dbo]. [ CounterService] para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="05c9a-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="05c9a-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="05c9a-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="05c9a-154">Usando o elemento de configuração SqlWorkflowInstanceStorePromotion</span><span class="sxs-lookup"><span data-stu-id="05c9a-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="05c9a-155">O elemento de configuração `SqlWorkflowInstanceStorePromotion` herda do elemento de configuração `SqlWorkflowInstanceStore` , mas adiciona um elemento de configuração adicional chamado `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="05c9a-156">O elemento de `promotionSets` permite que o usuário para especificar propriedades elevadas com a configuração.</span><span class="sxs-lookup"><span data-stu-id="05c9a-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="05c9a-157">Este é o arquivo de configuração que é usado por exemplo:</span><span class="sxs-lookup"><span data-stu-id="05c9a-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="05c9a-158">Examine a definição para dbo []. O modo de CounterService [].</span><span class="sxs-lookup"><span data-stu-id="05c9a-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="05c9a-159">Quando uma instância de fluxo de trabalho persistir, uma linha está inserida no modo de `InstancePromotedProperties` para cada `PromotionSet` definida na configuração.</span><span class="sxs-lookup"><span data-stu-id="05c9a-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="05c9a-160">Esta linha contém todas as propriedades elevadas de `PromotionSet` (uma propriedade promovida pela coluna).</span><span class="sxs-lookup"><span data-stu-id="05c9a-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="05c9a-161">Este `PromotionSet` é fechado por tuple: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="05c9a-162">Nesse exemplo, temos um `PromotionSet` definido na configuração cujo atributo de nome é `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="05c9a-163">Observe como o valor da coluna de `PromotionName` é igual ao atributo nome do elemento de `PromotionSet` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="05c9a-164">A ordem dos elementos de `promotedValue` correlaciona com o posicionamento propriedades elevadas no modo de `InstancePromotedProperties` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="05c9a-165">`Count` é o primeiro elemento de `promotedValue` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="05c9a-166">Como resultado, é mapeado para a coluna de `Value1` no modo de `InstancePromotedProperties` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="05c9a-167">`LastIncrementedAt` é o segundo elemento de `promotedValue` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="05c9a-168">Como resultado, é mapeado para a coluna de `Value2` no modo de `InstancePromotedProperties` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="05c9a-169">Usando a atividade de PromoteValue</span><span class="sxs-lookup"><span data-stu-id="05c9a-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="05c9a-170">Examine o arquivo CounterService.xamlx no Designer de base de fluxo de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="05c9a-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="05c9a-171">Observe que há duas atividades especiais na definição de WF: `PromoteValue<DateTime>` e `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="05c9a-172">A atividade de `PromoteValue<Int32>` tem seu membro de `Name` definido como `Count`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="05c9a-173">Isso corresponde com o primeiro elemento de `promotedValue` na configuração, e tem seu `Value` definida como a variável de fluxo de trabalho de `Counter` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="05c9a-174">Quando o fluxo de trabalho persistir, a variável de fluxo de trabalho de `Counter` é persistida como uma propriedade promovida na coluna de `Value1` do modo de `InstancePromotedProperties` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="05c9a-175">A atividade de `PromoteValue<DateTime>` tem seu membro de `Name` definido como `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="05c9a-176">Isso corresponde com o segundo elemento de `promotedValue` na configuração, e tem seu `Value` definida como a variável de fluxo de trabalho de `TimeLastIncremented` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="05c9a-177">Isso significa que quando o fluxo de trabalho persistir, o valor da variável de fluxo de trabalho de `TimeLastIncremented` será persistente como uma propriedade promovida na coluna de `Value2` do modo de `InstancePromotedProperties` .</span><span class="sxs-lookup"><span data-stu-id="05c9a-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="05c9a-178">Observe que a atividade de `PromotedValue` também tem um membro chamado booleano `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="05c9a-179">Quando esse membro é definido como `true`, este limpa todos os valores de propriedade elevados até esse ponto no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="05c9a-180">Por exemplo, se uma atividade da sequência é definida como segue:</span><span class="sxs-lookup"><span data-stu-id="05c9a-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="05c9a-181">PromoteValue {nome = "Conta", valor = 3}</span><span class="sxs-lookup"><span data-stu-id="05c9a-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="05c9a-182">PromoteValue {nome = "LastIncrementedAt", valor = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="05c9a-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="05c9a-183">Persistir</span><span class="sxs-lookup"><span data-stu-id="05c9a-183">Persist</span></span>  
  
4.  <span data-ttu-id="05c9a-184">PromoteValue {nome = "Conta", valor = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="05c9a-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="05c9a-185">Persistir</span><span class="sxs-lookup"><span data-stu-id="05c9a-185">Persist</span></span>  
  
 <span data-ttu-id="05c9a-186">No segundo persistir, o valor alto para `Count` será 4.</span><span class="sxs-lookup"><span data-stu-id="05c9a-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="05c9a-187">No entanto, o valor promovido para `LastIncrementedAt` será `NULL`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="05c9a-188">Se `ClearExistingPromotedData` não foi definido como `true` para a etapa 4, então após o segundo persistir, o valor alto para a contagem seria 4.</span><span class="sxs-lookup"><span data-stu-id="05c9a-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="05c9a-189">Como resultado, o valor alto para `LastIncrementedAt` seria ainda 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="05c9a-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="05c9a-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="05c9a-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="05c9a-191">Esta biblioteca de classe contém as seguintes classes públicas para simplificar o uso de recurso da promoção de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .</span><span class="sxs-lookup"><span data-stu-id="05c9a-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="05c9a-192">Classe de PromoteValue</span><span class="sxs-lookup"><span data-stu-id="05c9a-192">PromoteValue Class</span></span>  
 <span data-ttu-id="05c9a-193">Essa classe promove uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="05c9a-193">This class promotes one property.</span></span> <span data-ttu-id="05c9a-194">O nome da propriedade promovida deve corresponder um atributo nome de um elemento de `promotedValue` na configuração.</span><span class="sxs-lookup"><span data-stu-id="05c9a-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="05c9a-195">Esta atividade pode ser usada em Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="05c9a-196">Consulte o CounterServiceApplication para um uso de exemplo.</span><span class="sxs-lookup"><span data-stu-id="05c9a-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="05c9a-197">ClearExistingPromotedData (Bool)</span><span class="sxs-lookup"><span data-stu-id="05c9a-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="05c9a-198">Limpa todos os valores que foram valores antes desta atividade.</span><span class="sxs-lookup"><span data-stu-id="05c9a-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="05c9a-199">Nome (cadeia de caracteres)</span><span class="sxs-lookup"><span data-stu-id="05c9a-199">Name (string)</span></span>  
 <span data-ttu-id="05c9a-200">O nome que representa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="05c9a-200">The name that represents this property.</span></span> <span data-ttu-id="05c9a-201">Isso deve corresponder o atributo de nome de um \<promotedValue > elemento na configuração.</span><span class="sxs-lookup"><span data-stu-id="05c9a-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="05c9a-202">Valor (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="05c9a-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="05c9a-203">A variável/valor que você deseja armazenar na coluna.</span><span class="sxs-lookup"><span data-stu-id="05c9a-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="05c9a-204">Classe de PromoteValues</span><span class="sxs-lookup"><span data-stu-id="05c9a-204">PromoteValues Class</span></span>  
 <span data-ttu-id="05c9a-205">Promove várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="05c9a-205">Promotes multiple properties.</span></span> <span data-ttu-id="05c9a-206">Os nomes das propriedades elevadas devem corresponder todos os atributos de nome em elementos de `promotedValue` na configuração.</span><span class="sxs-lookup"><span data-stu-id="05c9a-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="05c9a-207">O uso é semelhante à atividade de `PromoteValue` , exceto pelo fato de que as várias propriedades podem ser elevadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="05c9a-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="05c9a-208">Esta atividade não pode ser usada em Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="05c9a-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="05c9a-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="05c9a-210">Deriva de `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="05c9a-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="05c9a-211">Essa classe derivada adiciona um participante personalizado de persistência (também uma parte desta biblioteca) como uma extensão de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="05c9a-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="05c9a-212">A implementação das atividades anteriores de fluxo de trabalho confia neste participante personalizado de persistência.</span><span class="sxs-lookup"><span data-stu-id="05c9a-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="05c9a-213">Esta biblioteca de classes também contém a implementação de `ConfigurationElement` para `SqlWorkflowInstanceStorePromotionElement` e um participante personalizado de persistência usado por atividades anteriores da promoção.</span><span class="sxs-lookup"><span data-stu-id="05c9a-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="05c9a-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="05c9a-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="05c9a-215">Este arquivo SQL cria um modo de exibição de `[dbo].[CounterService]` além da o modo de `[InstancePromotedProperties]` para ver todas as instâncias que têm uma promoção de CounterService definida.</span><span class="sxs-lookup"><span data-stu-id="05c9a-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05c9a-216">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="05c9a-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="05c9a-217">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="05c9a-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05c9a-218">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="05c9a-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05c9a-219">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="05c9a-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="05c9a-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05c9a-220">See Also</span></span>  
 [<span data-ttu-id="05c9a-221">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="05c9a-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
