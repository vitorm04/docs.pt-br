---
title: Ponto de extremidade
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452921"
---
# <a name="endpoint"></a><span data-ttu-id="a98b1-102">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="a98b1-102">Endpoint</span></span>
<span data-ttu-id="a98b1-103">Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="a98b1-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a98b1-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="a98b1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a98b1-105">Methods</span></span>  
 <span data-ttu-id="a98b1-106">A classe de ponto de extremidade define o método a seguir.</span><span class="sxs-lookup"><span data-stu-id="a98b1-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="a98b1-107">Método</span><span class="sxs-lookup"><span data-stu-id="a98b1-107">Method</span></span>|<span data-ttu-id="a98b1-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a98b1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a98b1-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="a98b1-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="a98b1-110">Recupera o nome de instância do contador de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="a98b1-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="a98b1-111">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a98b1-111">Properties</span></span>  
 <span data-ttu-id="a98b1-112">A classe de ponto de extremidade tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a98b1-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="a98b1-113">Endereço</span><span class="sxs-lookup"><span data-stu-id="a98b1-113">Address</span></span>  
 <span data-ttu-id="a98b1-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-114">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-116">Um URI que contém o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="a98b1-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="a98b1-117">AddressHeaders</span></span>  
 <span data-ttu-id="a98b1-118">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-118">Data type: string array</span></span>  
  
 <span data-ttu-id="a98b1-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-120">A coleção de cabeçalhos de endereço anexados a esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="a98b1-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="a98b1-121">AddressIdentity</span></span>  
 <span data-ttu-id="a98b1-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-122">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-124">A identidade do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="a98b1-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="a98b1-125">AppDomainId</span></span>  
 <span data-ttu-id="a98b1-126">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a98b1-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="a98b1-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-128">A id appdomain do appdomain que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="a98b1-129">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="a98b1-129">Behaviors</span></span>  
 <span data-ttu-id="a98b1-130">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="a98b1-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="a98b1-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-132">A coleção de comportamentos implementados por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="a98b1-133">Associação</span><span class="sxs-lookup"><span data-stu-id="a98b1-133">Binding</span></span>  
 <span data-ttu-id="a98b1-134">Tipo de dados: associação</span><span class="sxs-lookup"><span data-stu-id="a98b1-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="a98b1-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-136">A associação usada por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="a98b1-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="a98b1-137">ContractName</span></span>  
 <span data-ttu-id="a98b1-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-138">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-140">Uma cadeia de caracteres que especifica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="a98b1-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="a98b1-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="a98b1-141">CounterInstanceName</span></span>  
 <span data-ttu-id="a98b1-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-142">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-144">O nome da instância de contadores de desempenho do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="a98b1-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="a98b1-145">ListenUri</span></span>  
 <span data-ttu-id="a98b1-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-146">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-148">O Uri do ponto de extremidade de escuta.</span><span class="sxs-lookup"><span data-stu-id="a98b1-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a98b1-149">Nome</span><span class="sxs-lookup"><span data-stu-id="a98b1-149">Name</span></span>  
 <span data-ttu-id="a98b1-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a98b1-150">Data type: string</span></span>  
  
 <span data-ttu-id="a98b1-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-152">O nome exclusivo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="a98b1-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="a98b1-153">ProcessId</span></span>  
 <span data-ttu-id="a98b1-154">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a98b1-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="a98b1-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-156">O processo de identificação do processo que hospeda o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a98b1-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a98b1-157">ref</span><span class="sxs-lookup"><span data-stu-id="a98b1-157">ref</span></span>  
 <span data-ttu-id="a98b1-158">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="a98b1-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="a98b1-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a98b1-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a98b1-160">O contrato que esse ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="a98b1-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a98b1-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a98b1-161">Requirements</span></span>  
  
|<span data-ttu-id="a98b1-162">MOF</span><span class="sxs-lookup"><span data-stu-id="a98b1-162">MOF</span></span>|<span data-ttu-id="a98b1-163">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a98b1-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a98b1-164">Namespace</span><span class="sxs-lookup"><span data-stu-id="a98b1-164">Namespace</span></span>|<span data-ttu-id="a98b1-165">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a98b1-165">Defined in root\ServiceModel</span></span>|
