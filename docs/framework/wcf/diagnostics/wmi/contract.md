---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a><span data-ttu-id="c01d2-102">Contrato</span><span class="sxs-lookup"><span data-stu-id="c01d2-102">Contract</span></span>
<span data-ttu-id="c01d2-103">Contrato</span><span class="sxs-lookup"><span data-stu-id="c01d2-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c01d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c01d2-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="c01d2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c01d2-105">Methods</span></span>  
 <span data-ttu-id="c01d2-106">A classe de contrato não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c01d2-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c01d2-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c01d2-107">Properties</span></span>  
 <span data-ttu-id="c01d2-108">A classe de contrato tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c01d2-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="c01d2-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="c01d2-109">AppDomainId</span></span>  
 <span data-ttu-id="c01d2-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c01d2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c01d2-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-112">A identificação appdomain do appdomain que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="c01d2-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="c01d2-113">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="c01d2-113">Behaviors</span></span>  
 <span data-ttu-id="c01d2-114">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="c01d2-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="c01d2-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-116">Os comportamentos associados a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="c01d2-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="c01d2-117">Nome</span><span class="sxs-lookup"><span data-stu-id="c01d2-117">Name</span></span>  
 <span data-ttu-id="c01d2-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d2-118">Data type: string</span></span>  
  
 <span data-ttu-id="c01d2-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-120">O nome do contrato em WSDL.</span><span class="sxs-lookup"><span data-stu-id="c01d2-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="c01d2-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="c01d2-121">Namespace</span></span>  
 <span data-ttu-id="c01d2-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d2-122">Data type: string</span></span>  
  
 <span data-ttu-id="c01d2-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-124">O namespace do `portType` elemento em WSDL.</span><span class="sxs-lookup"><span data-stu-id="c01d2-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="c01d2-125">Operações</span><span class="sxs-lookup"><span data-stu-id="c01d2-125">Operations</span></span>  
 <span data-ttu-id="c01d2-126">Tipo de dados: matriz de operação</span><span class="sxs-lookup"><span data-stu-id="c01d2-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="c01d2-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-128">As operações desse contrato.</span><span class="sxs-lookup"><span data-stu-id="c01d2-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="c01d2-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="c01d2-129">ProcessId</span></span>  
 <span data-ttu-id="c01d2-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c01d2-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="c01d2-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-132">O processo de identificação do processo que hospeda o contrato.</span><span class="sxs-lookup"><span data-stu-id="c01d2-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="c01d2-133">ref</span><span class="sxs-lookup"><span data-stu-id="c01d2-133">ref</span></span>  
 <span data-ttu-id="c01d2-134">Tipo de dados: contrato</span><span class="sxs-lookup"><span data-stu-id="c01d2-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="c01d2-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-136">O tipo de retorno de chamada quando o contrato é um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="c01d2-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="c01d2-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="c01d2-137">SessionMode</span></span>  
 <span data-ttu-id="c01d2-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d2-138">Data type: string</span></span>  
  
 <span data-ttu-id="c01d2-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-140">Indica se o contrato requer a associação associada a esse contrato use sessões do canal.</span><span class="sxs-lookup"><span data-stu-id="c01d2-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="c01d2-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="c01d2-141">Type</span></span>  
 <span data-ttu-id="c01d2-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c01d2-142">Data type: string</span></span>  
  
 <span data-ttu-id="c01d2-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c01d2-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c01d2-144">O tipo do contrato.</span><span class="sxs-lookup"><span data-stu-id="c01d2-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c01d2-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c01d2-145">Requirements</span></span>  
  
|<span data-ttu-id="c01d2-146">MOF</span><span class="sxs-lookup"><span data-stu-id="c01d2-146">MOF</span></span>|<span data-ttu-id="c01d2-147">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c01d2-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c01d2-148">Namespace</span><span class="sxs-lookup"><span data-stu-id="c01d2-148">Namespace</span></span>|<span data-ttu-id="c01d2-149">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c01d2-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c01d2-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c01d2-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
