---
title: Contrato
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868431"
---
# <a name="contract"></a><span data-ttu-id="3a79c-102">Contrato</span><span class="sxs-lookup"><span data-stu-id="3a79c-102">Contract</span></span>
<span data-ttu-id="3a79c-103">Contrato</span><span class="sxs-lookup"><span data-stu-id="3a79c-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a79c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a79c-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3a79c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a79c-105">Methods</span></span>  
 <span data-ttu-id="3a79c-106">A classe Contract não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="3a79c-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a79c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3a79c-107">Properties</span></span>  
 <span data-ttu-id="3a79c-108">A classe Contract tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3a79c-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="3a79c-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="3a79c-109">AppDomainId</span></span>  
 <span data-ttu-id="3a79c-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="3a79c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="3a79c-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-112">A ID de AppDomain do AppDomain que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="3a79c-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="3a79c-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="3a79c-113">Behaviors</span></span>  
 <span data-ttu-id="3a79c-114">Tipo de dados: Matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="3a79c-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="3a79c-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-116">Os comportamentos associados a este contrato.</span><span class="sxs-lookup"><span data-stu-id="3a79c-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3a79c-117">Nome</span><span class="sxs-lookup"><span data-stu-id="3a79c-117">Name</span></span>  
 <span data-ttu-id="3a79c-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3a79c-118">Data type: string</span></span>  
  
 <span data-ttu-id="3a79c-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-120">O nome do contrato em WSDL.</span><span class="sxs-lookup"><span data-stu-id="3a79c-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="3a79c-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="3a79c-121">Namespace</span></span>  
 <span data-ttu-id="3a79c-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3a79c-122">Data type: string</span></span>  
  
 <span data-ttu-id="3a79c-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-124">O namespace do `portType` elemento no WSDL.</span><span class="sxs-lookup"><span data-stu-id="3a79c-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="3a79c-125">Operações</span><span class="sxs-lookup"><span data-stu-id="3a79c-125">Operations</span></span>  
 <span data-ttu-id="3a79c-126">Tipo de dados: Matriz de operação</span><span class="sxs-lookup"><span data-stu-id="3a79c-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="3a79c-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-128">As operações deste contrato.</span><span class="sxs-lookup"><span data-stu-id="3a79c-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="3a79c-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="3a79c-129">ProcessId</span></span>  
 <span data-ttu-id="3a79c-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="3a79c-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="3a79c-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-132">A ID do processo que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="3a79c-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3a79c-133">ref</span><span class="sxs-lookup"><span data-stu-id="3a79c-133">ref</span></span>  
 <span data-ttu-id="3a79c-134">Tipo de dados: Contrato</span><span class="sxs-lookup"><span data-stu-id="3a79c-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="3a79c-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-136">O tipo de retorno de chamada quando o contrato é um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="3a79c-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="3a79c-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="3a79c-137">SessionMode</span></span>  
 <span data-ttu-id="3a79c-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3a79c-138">Data type: string</span></span>  
  
 <span data-ttu-id="3a79c-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-140">Indica se o contrato requer que a associação associada a este contrato use sessões de canal.</span><span class="sxs-lookup"><span data-stu-id="3a79c-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="3a79c-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="3a79c-141">Type</span></span>  
 <span data-ttu-id="3a79c-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3a79c-142">Data type: string</span></span>  
  
 <span data-ttu-id="3a79c-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3a79c-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a79c-144">O tipo do contrato.</span><span class="sxs-lookup"><span data-stu-id="3a79c-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a79c-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a79c-145">Requirements</span></span>  
  
|<span data-ttu-id="3a79c-146">MOF</span><span class="sxs-lookup"><span data-stu-id="3a79c-146">MOF</span></span>|<span data-ttu-id="3a79c-147">Declarado em ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="3a79c-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3a79c-148">Namespace</span><span class="sxs-lookup"><span data-stu-id="3a79c-148">Namespace</span></span>|<span data-ttu-id="3a79c-149">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3a79c-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a79c-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a79c-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
