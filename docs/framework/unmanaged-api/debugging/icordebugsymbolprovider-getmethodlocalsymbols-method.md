---
title: "Método ICorDebugSymbolProvider::GetMethodLocalSymbols"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3533157f25bda881fdbd0c77186c590d5a49f8c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="1b2bb-102">Método ICorDebugSymbolProvider::GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="1b2bb-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="1b2bb-103">Obtém os símbolos do local do método recebe o endereço virtual relativo (RVA) do método.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b2bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b2bb-104">Syntax</span></span>  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b2bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b2bb-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="1b2bb-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="1b2bb-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="1b2bb-108">[out] Um ponteiro para o número de símbolos recuperada pelo método.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="1b2bb-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém os símbolos de local do método.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b2bb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b2bb-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b2bb-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1b2bb-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b2bb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b2bb-112">Requirements</span></span>  
 <span data-ttu-id="1b2bb-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b2bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b2bb-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b2bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b2bb-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b2bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b2bb-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b2bb-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2bb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b2bb-117">See Also</span></span>  
 [<span data-ttu-id="1b2bb-118">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="1b2bb-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)  
 [<span data-ttu-id="1b2bb-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1b2bb-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="1b2bb-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="1b2bb-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
