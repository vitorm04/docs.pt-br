---
title: Ponto de extremidade
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487640"
---
# <a name="endpoint"></a><span data-ttu-id="7186f-102">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="7186f-102">Endpoint</span></span>
<span data-ttu-id="7186f-103">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="7186f-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7186f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7186f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7186f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7186f-105">Methods</span></span>  
 <span data-ttu-id="7186f-106">A classe de ponto de extremidade define o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="7186f-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="7186f-107">Método</span><span class="sxs-lookup"><span data-stu-id="7186f-107">Method</span></span>|<span data-ttu-id="7186f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7186f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7186f-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="7186f-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="7186f-110">Recupera o nome de instância do contador de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="7186f-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="7186f-111">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7186f-111">Properties</span></span>  
 <span data-ttu-id="7186f-112">A classe de ponto de extremidade tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7186f-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="7186f-113">Endereço</span><span class="sxs-lookup"><span data-stu-id="7186f-113">Address</span></span>  
 <span data-ttu-id="7186f-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-114">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-116">Um URI que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="7186f-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="7186f-117">AddressHeaders</span></span>  
 <span data-ttu-id="7186f-118">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-118">Data type: string array</span></span>  
  
 <span data-ttu-id="7186f-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-120">A coleção de cabeçalhos de endereço anexados a esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="7186f-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="7186f-121">AddressIdentity</span></span>  
 <span data-ttu-id="7186f-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-122">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-124">A identidade do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="7186f-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="7186f-125">AppDomainId</span></span>  
 <span data-ttu-id="7186f-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7186f-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="7186f-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-128">A identificação appdomain do appdomain que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="7186f-129">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="7186f-129">Behaviors</span></span>  
 <span data-ttu-id="7186f-130">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="7186f-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="7186f-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-132">A coleção de comportamentos implementados por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="7186f-133">Associação</span><span class="sxs-lookup"><span data-stu-id="7186f-133">Binding</span></span>  
 <span data-ttu-id="7186f-134">Tipo de dados: associação</span><span class="sxs-lookup"><span data-stu-id="7186f-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="7186f-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-136">A associação usada por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="7186f-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="7186f-137">ContractName</span></span>  
 <span data-ttu-id="7186f-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-138">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-140">Uma cadeia de caracteres que especifica qual contrato esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="7186f-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="7186f-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="7186f-141">CounterInstanceName</span></span>  
 <span data-ttu-id="7186f-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-142">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-144">O nome da instância de contadores de desempenho do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="7186f-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="7186f-145">ListenUri</span></span>  
 <span data-ttu-id="7186f-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-146">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-148">O Uri do ponto de extremidade de escuta.</span><span class="sxs-lookup"><span data-stu-id="7186f-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7186f-149">Nome</span><span class="sxs-lookup"><span data-stu-id="7186f-149">Name</span></span>  
 <span data-ttu-id="7186f-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7186f-150">Data type: string</span></span>  
  
 <span data-ttu-id="7186f-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-152">O nome exclusivo desse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="7186f-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="7186f-153">ProcessId</span></span>  
 <span data-ttu-id="7186f-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7186f-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="7186f-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-156">O processo de identificação do processo que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="7186f-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="7186f-157">ref</span><span class="sxs-lookup"><span data-stu-id="7186f-157">ref</span></span>  
 <span data-ttu-id="7186f-158">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="7186f-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="7186f-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7186f-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7186f-160">O contrato que esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="7186f-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7186f-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7186f-161">Requirements</span></span>  
  
|<span data-ttu-id="7186f-162">MOF</span><span class="sxs-lookup"><span data-stu-id="7186f-162">MOF</span></span>|<span data-ttu-id="7186f-163">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7186f-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7186f-164">Namespace</span><span class="sxs-lookup"><span data-stu-id="7186f-164">Namespace</span></span>|<span data-ttu-id="7186f-165">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7186f-165">Defined in root\ServiceModel</span></span>|
