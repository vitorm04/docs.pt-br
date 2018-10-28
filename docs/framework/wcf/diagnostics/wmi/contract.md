---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12e9cbf5232ebbad33ccc4fdca33233997d27357
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194664"
---
# <a name="contract"></a><span data-ttu-id="2fdb3-102">Contrato</span><span class="sxs-lookup"><span data-stu-id="2fdb3-102">Contract</span></span>
<span data-ttu-id="2fdb3-103">Contrato</span><span class="sxs-lookup"><span data-stu-id="2fdb3-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fdb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fdb3-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2fdb3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2fdb3-105">Methods</span></span>  
 <span data-ttu-id="2fdb3-106">A classe de contrato não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2fdb3-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2fdb3-107">Properties</span></span>  
 <span data-ttu-id="2fdb3-108">A classe de contrato tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2fdb3-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="2fdb3-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="2fdb3-109">AppDomainId</span></span>  
 <span data-ttu-id="2fdb3-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2fdb3-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fdb3-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-112">A id appdomain do appdomain que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="2fdb3-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="2fdb3-113">Behaviors</span></span>  
 <span data-ttu-id="2fdb3-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="2fdb3-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="2fdb3-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-116">Os comportamentos associados a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="2fdb3-117">Nome</span><span class="sxs-lookup"><span data-stu-id="2fdb3-117">Name</span></span>  
 <span data-ttu-id="2fdb3-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2fdb3-118">Data type: string</span></span>  
  
 <span data-ttu-id="2fdb3-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-120">O nome do contrato em WSDL.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="2fdb3-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="2fdb3-121">Namespace</span></span>  
 <span data-ttu-id="2fdb3-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2fdb3-122">Data type: string</span></span>  
  
 <span data-ttu-id="2fdb3-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-124">O namespace do `portType` elemento no WSDL.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="2fdb3-125">Operações</span><span class="sxs-lookup"><span data-stu-id="2fdb3-125">Operations</span></span>  
 <span data-ttu-id="2fdb3-126">Tipo de dados: matriz de operação</span><span class="sxs-lookup"><span data-stu-id="2fdb3-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="2fdb3-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-128">As operações do contrato.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="2fdb3-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="2fdb3-129">ProcessId</span></span>  
 <span data-ttu-id="2fdb3-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="2fdb3-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fdb3-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-132">O processo de identificação do processo que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="2fdb3-133">ref</span><span class="sxs-lookup"><span data-stu-id="2fdb3-133">ref</span></span>  
 <span data-ttu-id="2fdb3-134">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="2fdb3-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="2fdb3-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-136">O tipo de retorno de chamada quando o contrato é um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="2fdb3-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="2fdb3-137">SessionMode</span></span>  
 <span data-ttu-id="2fdb3-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2fdb3-138">Data type: string</span></span>  
  
 <span data-ttu-id="2fdb3-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-140">Indica se o contrato requer a associação associada a este contrato para usar sessões de canal.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="2fdb3-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="2fdb3-141">Type</span></span>  
 <span data-ttu-id="2fdb3-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2fdb3-142">Data type: string</span></span>  
  
 <span data-ttu-id="2fdb3-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2fdb3-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fdb3-144">O tipo do contrato.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fdb3-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fdb3-145">Requirements</span></span>  
  
|<span data-ttu-id="2fdb3-146">MOF</span><span class="sxs-lookup"><span data-stu-id="2fdb3-146">MOF</span></span>|<span data-ttu-id="2fdb3-147">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2fdb3-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2fdb3-148">Namespace</span><span class="sxs-lookup"><span data-stu-id="2fdb3-148">Namespace</span></span>|<span data-ttu-id="2fdb3-149">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2fdb3-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fdb3-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fdb3-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
