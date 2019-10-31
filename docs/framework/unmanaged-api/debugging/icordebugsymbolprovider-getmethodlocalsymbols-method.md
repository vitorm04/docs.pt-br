---
title: 'Método ICorDebugSymbolProvider:: GetMethodLocalSymbols'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 6cd04ea7f83fb7ae96d9ffd1beba39530511ec25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138900"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="52f55-102">Método ICorDebugSymbolProvider:: GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="52f55-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="52f55-103">Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="52f55-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52f55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52f55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52f55-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="52f55-106">no O endereço virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="52f55-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="52f55-107">no O número de símbolos locais solicitados.</span><span class="sxs-lookup"><span data-stu-id="52f55-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="52f55-108">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="52f55-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="52f55-109">fora Um ponteiro para uma matriz [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) que contém os símbolos locais do método.</span><span class="sxs-lookup"><span data-stu-id="52f55-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f55-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="52f55-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52f55-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="52f55-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f55-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52f55-112">Requirements</span></span>  
 <span data-ttu-id="52f55-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f55-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f55-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52f55-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52f55-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f55-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f55-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f55-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f55-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52f55-117">See also</span></span>

- [<span data-ttu-id="52f55-118">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="52f55-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="52f55-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="52f55-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="52f55-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="52f55-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
