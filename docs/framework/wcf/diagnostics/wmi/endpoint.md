---
title: Ponto de extremidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bcb02ae01d66830d9bfd486c5ae3941c45c2a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint"></a><span data-ttu-id="b7ebf-102">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b7ebf-102">Endpoint</span></span>
<span data-ttu-id="b7ebf-103">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b7ebf-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ebf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7ebf-104">Syntax</span></span>  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b7ebf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b7ebf-105">Methods</span></span>  
 <span data-ttu-id="b7ebf-106">A classe de ponto de extremidade define o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="b7ebf-107">Método</span><span class="sxs-lookup"><span data-stu-id="b7ebf-107">Method</span></span>|<span data-ttu-id="b7ebf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7ebf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7ebf-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="b7ebf-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="b7ebf-110">Recupera o nome de instância do contador de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="b7ebf-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="b7ebf-111">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b7ebf-111">Properties</span></span>  
 <span data-ttu-id="b7ebf-112">A classe de ponto de extremidade tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b7ebf-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="b7ebf-113">Endereço</span><span class="sxs-lookup"><span data-stu-id="b7ebf-113">Address</span></span>  
 <span data-ttu-id="b7ebf-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-114">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-116">Um URI que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="b7ebf-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="b7ebf-117">AddressHeaders</span></span>  
 <span data-ttu-id="b7ebf-118">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-118">Data type: string array</span></span>  
  
 <span data-ttu-id="b7ebf-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-120">A coleção de cabeçalhos de endereço anexados a esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="b7ebf-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="b7ebf-121">AddressIdentity</span></span>  
 <span data-ttu-id="b7ebf-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-122">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-124">A identidade do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="b7ebf-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="b7ebf-125">AppDomainId</span></span>  
 <span data-ttu-id="b7ebf-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b7ebf-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="b7ebf-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-128">A identificação appdomain do appdomain que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="b7ebf-129">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="b7ebf-129">Behaviors</span></span>  
 <span data-ttu-id="b7ebf-130">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="b7ebf-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="b7ebf-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-132">A coleção de comportamentos implementados por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="b7ebf-133">Associação</span><span class="sxs-lookup"><span data-stu-id="b7ebf-133">Binding</span></span>  
 <span data-ttu-id="b7ebf-134">Tipo de dados: associação</span><span class="sxs-lookup"><span data-stu-id="b7ebf-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="b7ebf-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-136">A associação usada por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="b7ebf-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="b7ebf-137">ContractName</span></span>  
 <span data-ttu-id="b7ebf-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-138">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-140">Uma cadeia de caracteres que especifica qual contrato esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="b7ebf-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="b7ebf-141">CounterInstanceName</span></span>  
 <span data-ttu-id="b7ebf-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-142">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-144">O nome da instância de contadores de desempenho do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="b7ebf-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="b7ebf-145">ListenUri</span></span>  
 <span data-ttu-id="b7ebf-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-146">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-148">O Uri do ponto de extremidade de escuta.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="b7ebf-149">Nome</span><span class="sxs-lookup"><span data-stu-id="b7ebf-149">Name</span></span>  
 <span data-ttu-id="b7ebf-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7ebf-150">Data type: string</span></span>  
  
 <span data-ttu-id="b7ebf-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-152">O nome exclusivo desse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="b7ebf-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="b7ebf-153">ProcessId</span></span>  
 <span data-ttu-id="b7ebf-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b7ebf-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="b7ebf-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-156">O processo de identificação do processo que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b7ebf-157">ref</span><span class="sxs-lookup"><span data-stu-id="b7ebf-157">ref</span></span>  
 <span data-ttu-id="b7ebf-158">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="b7ebf-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="b7ebf-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7ebf-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7ebf-160">O contrato que esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ebf-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7ebf-161">Requirements</span></span>  
  
|<span data-ttu-id="b7ebf-162">MOF</span><span class="sxs-lookup"><span data-stu-id="b7ebf-162">MOF</span></span>|<span data-ttu-id="b7ebf-163">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b7ebf-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b7ebf-164">Namespace</span><span class="sxs-lookup"><span data-stu-id="b7ebf-164">Namespace</span></span>|<span data-ttu-id="b7ebf-165">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b7ebf-165">Defined in root\ServiceModel</span></span>|
