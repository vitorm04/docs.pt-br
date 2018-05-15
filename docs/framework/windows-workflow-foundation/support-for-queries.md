---
title: Suporte para consultas
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 5c46ed5ae2fc2cc2275bfa7251fe5f8fa346c1f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="support-for-queries"></a><span data-ttu-id="dfed5-102">Suporte para consultas</span><span class="sxs-lookup"><span data-stu-id="dfed5-102">Support for Queries</span></span>
<span data-ttu-id="dfed5-103">A instância Store de fluxo de trabalho do SQL registra um conjunto de propriedades conhecidos no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="dfed5-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="dfed5-104">Os usuários podem ver para as instâncias com base nessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="dfed5-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="dfed5-105">A lista a seguir contém algumas dessas propriedades conhecidas:</span><span class="sxs-lookup"><span data-stu-id="dfed5-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="dfed5-106">**Nome do site.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-106">**Site Name.**</span></span> <span data-ttu-id="dfed5-107">Nome do site que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="dfed5-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="dfed5-108">**Caminho relativo de aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-108">**Relative Application Path.**</span></span> <span data-ttu-id="dfed5-109">Caminho do aplicativo relativa ao site.</span><span class="sxs-lookup"><span data-stu-id="dfed5-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="dfed5-110">**Caminho relativo do serviço.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-110">**Relative Service Path.**</span></span> <span data-ttu-id="dfed5-111">Caminho do serviço relativo para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfed5-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="dfed5-112">**Nome do serviço.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-112">**Service Name.**</span></span> <span data-ttu-id="dfed5-113">Nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="dfed5-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="dfed5-114">**Namespace de serviço.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-114">**Service Namespace.**</span></span> <span data-ttu-id="dfed5-115">Nome do namespace que usa o serviço.</span><span class="sxs-lookup"><span data-stu-id="dfed5-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="dfed5-116">**Computador atual.**</span><span class="sxs-lookup"><span data-stu-id="dfed5-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="dfed5-117">**Máquina de última**.</span><span class="sxs-lookup"><span data-stu-id="dfed5-117">**Last Machine**.</span></span> <span data-ttu-id="dfed5-118">O computador no qual a instância do serviço de fluxo de trabalho executou a última vez.</span><span class="sxs-lookup"><span data-stu-id="dfed5-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfed5-119">Para cenários são hospedados usando o host de Serviço de Fluxo de Trabalho, somente as quatro propriedades mais recentes são preenchidas.</span><span class="sxs-lookup"><span data-stu-id="dfed5-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="dfed5-120">Para cenários de aplicativo de fluxo de trabalho, apenas a propriedade a última é preenchida.</span><span class="sxs-lookup"><span data-stu-id="dfed5-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="dfed5-121">O tempo de execução de fluxo de trabalho fornece valores para as primeiras três propriedades.</span><span class="sxs-lookup"><span data-stu-id="dfed5-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="dfed5-122">O host de serviço de fluxo de trabalho fornece o valor para o **motivo suspender** propriedade.</span><span class="sxs-lookup"><span data-stu-id="dfed5-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="dfed5-123">O armazenamento de instância de fluxo de trabalho do SQL em si fornece valores para o **última máquina atualizado** propriedade.</span><span class="sxs-lookup"><span data-stu-id="dfed5-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="dfed5-124">O recurso de Store de instância de fluxo de trabalho do SQL também permite que você especifique as propriedades personalizadas que você deseja armazenar os valores na base de dados de persistência e que você deseja usar em consultas.</span><span class="sxs-lookup"><span data-stu-id="dfed5-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="dfed5-125">Para obter mais informações sobre promoções personalizadas, consulte [repositório extensibilidade](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="dfed5-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="dfed5-126">Exibições</span><span class="sxs-lookup"><span data-stu-id="dfed5-126">Views</span></span>  
 <span data-ttu-id="dfed5-127">O armazenamento de instância contém as seguintes modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="dfed5-127">The instance store contains the following views.</span></span> <span data-ttu-id="dfed5-128">Consulte [esquema de banco de dados de persistência](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="dfed5-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="dfed5-129">O modo de instâncias</span><span class="sxs-lookup"><span data-stu-id="dfed5-129">The Instances View</span></span>  
 <span data-ttu-id="dfed5-130">O modo de instâncias contém os campos seguintes:</span><span class="sxs-lookup"><span data-stu-id="dfed5-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="dfed5-131">**Id**</span><span class="sxs-lookup"><span data-stu-id="dfed5-131">**Id**</span></span>  
  
2.  <span data-ttu-id="dfed5-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="dfed5-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="dfed5-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="dfed5-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="dfed5-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="dfed5-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="dfed5-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="dfed5-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="dfed5-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="dfed5-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="dfed5-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="dfed5-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="dfed5-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="dfed5-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="dfed5-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="dfed5-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="dfed5-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="dfed5-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="dfed5-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="dfed5-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="dfed5-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="dfed5-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="dfed5-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="dfed5-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="dfed5-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="dfed5-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="dfed5-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="dfed5-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="dfed5-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="dfed5-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="dfed5-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="dfed5-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="dfed5-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="dfed5-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="dfed5-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="dfed5-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="dfed5-150">O modo de ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="dfed5-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="dfed5-151">O modo de ServiceDeployments contém os campos seguintes:</span><span class="sxs-lookup"><span data-stu-id="dfed5-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="dfed5-152">**Nome do site**</span><span class="sxs-lookup"><span data-stu-id="dfed5-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="dfed5-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="dfed5-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="dfed5-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="dfed5-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="dfed5-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="dfed5-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="dfed5-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="dfed5-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="dfed5-157">O modo de InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="dfed5-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="dfed5-158">O modo de InstancePromotedProperties contém os seguintes campos.</span><span class="sxs-lookup"><span data-stu-id="dfed5-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="dfed5-159">Para obter detalhes sobre propriedades promovidas, consulte o [repositório extensibilidade](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="dfed5-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="dfed5-160">**instanceId**</span><span class="sxs-lookup"><span data-stu-id="dfed5-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="dfed5-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="dfed5-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="dfed5-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="dfed5-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="dfed5-163">**Valor #** (um conjunto de campos de **Value1** para **Value64**).</span><span class="sxs-lookup"><span data-stu-id="dfed5-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
