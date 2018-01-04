---
title: Interface ICorDebugSymbolProvider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63823c535ad4d036dd5d539c8fe5381d350ccbe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="14a4f-102">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="14a4f-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="14a4f-103">Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="14a4f-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14a4f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="14a4f-104">Methods</span></span>  
  
|<span data-ttu-id="14a4f-105">Método</span><span class="sxs-lookup"><span data-stu-id="14a4f-105">Method</span></span>|<span data-ttu-id="14a4f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="14a4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14a4f-107">Método GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="14a4f-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="14a4f-108">Lê dados de um assembly mesclado fornecido um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="14a4f-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="14a4f-109">Método GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="14a4f-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="14a4f-110">Retorna os metadados de um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="14a4f-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="14a4f-111">Método GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="14a4f-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="14a4f-112">Obtém o endereço de início do método e o tamanho fornecido um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="14a4f-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="14a4f-113">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="14a4f-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="14a4f-114">Obtém a instância de símbolos de campo que correspondem a uma assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="14a4f-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="14a4f-115">Método GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="14a4f-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="14a4f-116">Obtém os registros de símbolo para todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="14a4f-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="14a4f-117">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="14a4f-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="14a4f-118">Obtém os símbolos do local do método recebe o endereço virtual relativo (RVA) do método.</span><span class="sxs-lookup"><span data-stu-id="14a4f-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="14a4f-119">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="14a4f-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="14a4f-120">Obtém os símbolos de parâmetro do método recebe o endereço virtual relativo (RVA) do método.</span><span class="sxs-lookup"><span data-stu-id="14a4f-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="14a4f-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="14a4f-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="14a4f-122">Retorna informações sobre propriedades de método, como o método token de metadados e informações sobre seus parâmetros genéricos, dado um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="14a4f-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="14a4f-123">Método GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="14a4f-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="14a4f-124">Retorna o tamanho do objeto para um objeto com base em sua assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="14a4f-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="14a4f-125">Método GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="14a4f-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="14a4f-126">Obtém os símbolos de campo estático que correspondem a uma assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="14a4f-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="14a4f-127">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="14a4f-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="14a4f-128">Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, dado um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="14a4f-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14a4f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="14a4f-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14a4f-130">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14a4f-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="14a4f-131">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="14a4f-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a4f-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14a4f-132">Requirements</span></span>  
 <span data-ttu-id="14a4f-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a4f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a4f-134">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14a4f-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14a4f-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a4f-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a4f-136">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a4f-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a4f-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14a4f-137">See Also</span></span>  
 [<span data-ttu-id="14a4f-138">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="14a4f-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="14a4f-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="14a4f-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
