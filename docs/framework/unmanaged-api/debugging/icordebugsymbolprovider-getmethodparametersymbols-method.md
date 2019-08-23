---
title: 'Método ICorDebugSymbolProvider:: GetMethodParameterSymbols'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04262876db39dad93cf5904cdbb81b568fc22041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957331"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="a4d09-102">Método ICorDebugSymbolProvider:: GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="a4d09-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="a4d09-103">Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="a4d09-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d09-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4d09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d09-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4d09-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="a4d09-106">no O endereço virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="a4d09-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="a4d09-107">no O número de símbolos locais solicitados.</span><span class="sxs-lookup"><span data-stu-id="a4d09-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="a4d09-108">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="a4d09-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="a4d09-109">fora Um ponteiro para uma matriz [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) que contém os símbolos locais do método.</span><span class="sxs-lookup"><span data-stu-id="a4d09-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4d09-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4d09-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4d09-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a4d09-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d09-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4d09-112">Requirements</span></span>  
 <span data-ttu-id="a4d09-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d09-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d09-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4d09-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4d09-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4d09-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4d09-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d09-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d09-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4d09-117">See also</span></span>

- [<span data-ttu-id="a4d09-118">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="a4d09-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="a4d09-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="a4d09-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="a4d09-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a4d09-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
