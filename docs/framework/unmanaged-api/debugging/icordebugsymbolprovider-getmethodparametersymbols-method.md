---
title: "Método ICorDebugSymbolProvider::GetMethodParameterSymbols"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd3fc08eec9066f54d90fbe4824ce3f1a1c901dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="7a16c-102">Método ICorDebugSymbolProvider::GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="7a16c-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="7a16c-103">Obtém os símbolos de parâmetro do método recebe o endereço virtual relativo (RVA) do método.</span><span class="sxs-lookup"><span data-stu-id="7a16c-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a16c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a16c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a16c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a16c-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="7a16c-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="7a16c-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="7a16c-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="7a16c-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="7a16c-108">[out] Um ponteiro para o número de símbolos recuperada pelo método.</span><span class="sxs-lookup"><span data-stu-id="7a16c-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="7a16c-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém os símbolos de local do método.</span><span class="sxs-lookup"><span data-stu-id="7a16c-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a16c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a16c-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a16c-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7a16c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a16c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a16c-112">Requirements</span></span>  
 <span data-ttu-id="7a16c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a16c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a16c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a16c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a16c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a16c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a16c-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a16c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a16c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a16c-117">See Also</span></span>  
 [<span data-ttu-id="7a16c-118">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="7a16c-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [<span data-ttu-id="7a16c-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="7a16c-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="7a16c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7a16c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
