---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12e9cbf5232ebbad33ccc4fdca33233997d27357
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371557"
---
# <a name="contract"></a><span data-ttu-id="dbe6c-102">Contrato</span><span class="sxs-lookup"><span data-stu-id="dbe6c-102">Contract</span></span>
<span data-ttu-id="dbe6c-103">Contrato</span><span class="sxs-lookup"><span data-stu-id="dbe6c-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbe6c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="dbe6c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="dbe6c-105">Methods</span></span>  
 <span data-ttu-id="dbe6c-106">A classe de contrato não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dbe6c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dbe6c-107">Properties</span></span>  
 <span data-ttu-id="dbe6c-108">A classe de contrato tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="dbe6c-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="dbe6c-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="dbe6c-109">AppDomainId</span></span>  
 <span data-ttu-id="dbe6c-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="dbe6c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="dbe6c-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-112">A id appdomain do appdomain que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="dbe6c-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="dbe6c-113">Behaviors</span></span>  
 <span data-ttu-id="dbe6c-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="dbe6c-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="dbe6c-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-116">Os comportamentos associados a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="dbe6c-117">Nome</span><span class="sxs-lookup"><span data-stu-id="dbe6c-117">Name</span></span>  
 <span data-ttu-id="dbe6c-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="dbe6c-118">Data type: string</span></span>  
  
 <span data-ttu-id="dbe6c-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-120">O nome do contrato em WSDL.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="dbe6c-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="dbe6c-121">Namespace</span></span>  
 <span data-ttu-id="dbe6c-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="dbe6c-122">Data type: string</span></span>  
  
 <span data-ttu-id="dbe6c-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-124">O namespace do `portType` elemento no WSDL.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="dbe6c-125">Operações</span><span class="sxs-lookup"><span data-stu-id="dbe6c-125">Operations</span></span>  
 <span data-ttu-id="dbe6c-126">Tipo de dados: matriz de operação</span><span class="sxs-lookup"><span data-stu-id="dbe6c-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="dbe6c-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-128">As operações do contrato.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="dbe6c-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="dbe6c-129">ProcessId</span></span>  
 <span data-ttu-id="dbe6c-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="dbe6c-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="dbe6c-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-132">O processo de identificação do processo que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="dbe6c-133">ref</span><span class="sxs-lookup"><span data-stu-id="dbe6c-133">ref</span></span>  
 <span data-ttu-id="dbe6c-134">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="dbe6c-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="dbe6c-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-136">O tipo de retorno de chamada quando o contrato é um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="dbe6c-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="dbe6c-137">SessionMode</span></span>  
 <span data-ttu-id="dbe6c-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="dbe6c-138">Data type: string</span></span>  
  
 <span data-ttu-id="dbe6c-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-140">Indica se o contrato requer a associação associada a este contrato para usar sessões de canal.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="dbe6c-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbe6c-141">Type</span></span>  
 <span data-ttu-id="dbe6c-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="dbe6c-142">Data type: string</span></span>  
  
 <span data-ttu-id="dbe6c-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="dbe6c-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe6c-144">O tipo do contrato.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe6c-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbe6c-145">Requirements</span></span>  
  
|<span data-ttu-id="dbe6c-146">MOF</span><span class="sxs-lookup"><span data-stu-id="dbe6c-146">MOF</span></span>|<span data-ttu-id="dbe6c-147">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dbe6c-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dbe6c-148">Namespace</span><span class="sxs-lookup"><span data-stu-id="dbe6c-148">Namespace</span></span>|<span data-ttu-id="dbe6c-149">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dbe6c-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbe6c-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbe6c-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
