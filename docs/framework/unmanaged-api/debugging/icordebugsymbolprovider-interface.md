---
title: Interface ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 6f7a8a2b12c047b956a3b6e85fe8365e0360b3f2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791526"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="13bfe-102">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="13bfe-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="13bfe-103">Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração.</span><span class="sxs-lookup"><span data-stu-id="13bfe-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13bfe-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="13bfe-104">Methods</span></span>  
  
|<span data-ttu-id="13bfe-105">Método</span><span class="sxs-lookup"><span data-stu-id="13bfe-105">Method</span></span>|<span data-ttu-id="13bfe-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="13bfe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13bfe-107">Método GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="13bfe-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="13bfe-108">Lê dados de um assembly mesclado, dado um endereço virtual relativo (RVA) no assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="13bfe-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="13bfe-109">Método GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="13bfe-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="13bfe-110">Retorna os metadados de um assembly mesclado.</span><span class="sxs-lookup"><span data-stu-id="13bfe-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="13bfe-111">Método GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="13bfe-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="13bfe-112">Obtém o endereço inicial e o tamanho do método de acordo com um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="13bfe-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="13bfe-113">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="13bfe-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="13bfe-114">Obtém os símbolos de campo de instância que correspondem a uma assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="13bfe-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="13bfe-115">Método GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="13bfe-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="13bfe-116">Obtém os registros de símbolo de todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="13bfe-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="13bfe-117">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="13bfe-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="13bfe-118">Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="13bfe-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="13bfe-119">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="13bfe-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="13bfe-120">Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="13bfe-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="13bfe-121">Método GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="13bfe-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="13bfe-122">Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.</span><span class="sxs-lookup"><span data-stu-id="13bfe-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="13bfe-123">Método GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="13bfe-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="13bfe-124">Retorna o tamanho do objeto de um objeto com base em sua assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="13bfe-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="13bfe-125">Método GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="13bfe-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="13bfe-126">Obtém os símbolos de campo estático que correspondem a uma assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="13bfe-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="13bfe-127">Método GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="13bfe-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="13bfe-128">Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.</span><span class="sxs-lookup"><span data-stu-id="13bfe-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13bfe-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="13bfe-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13bfe-130">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="13bfe-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="13bfe-131">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="13bfe-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13bfe-132">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="13bfe-132">Requirements</span></span>  
 <span data-ttu-id="13bfe-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13bfe-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13bfe-134">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13bfe-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13bfe-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13bfe-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13bfe-136">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13bfe-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13bfe-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="13bfe-137">See also</span></span>

- [<span data-ttu-id="13bfe-138">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="13bfe-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="13bfe-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="13bfe-139">Debugging</span></span>](index.md)
