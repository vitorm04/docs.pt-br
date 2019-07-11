---
title: Método ICorDebugSymbolProvider::GetMethodLocalSymbols
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40123eff4028c1ebda898db27a5bd746571ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771400"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="e964e-102">Método ICorDebugSymbolProvider::GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="e964e-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="e964e-103">Obtém os símbolos de locais de um método considerando o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="e964e-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e964e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e964e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e964e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e964e-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="e964e-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="e964e-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="e964e-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="e964e-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e964e-108">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="e964e-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="e964e-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém símbolos de locais do método.</span><span class="sxs-lookup"><span data-stu-id="e964e-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e964e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e964e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e964e-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e964e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e964e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e964e-112">Requirements</span></span>  
 <span data-ttu-id="e964e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e964e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e964e-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e964e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e964e-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e964e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e964e-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e964e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e964e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e964e-117">See also</span></span>

- [<span data-ttu-id="e964e-118">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="e964e-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="e964e-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="e964e-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e964e-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e964e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
