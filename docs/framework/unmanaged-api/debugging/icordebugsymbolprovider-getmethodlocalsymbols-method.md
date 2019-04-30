---
title: Método ICorDebugSymbolProvider::GetMethodLocalSymbols
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99f76bd19ef274c3d4207fdd071914b736314a3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953316"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="30721-102">Método ICorDebugSymbolProvider::GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="30721-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="30721-103">Obtém os símbolos de locais de um método considerando o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="30721-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30721-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30721-104">Syntax</span></span>  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30721-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30721-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="30721-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="30721-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="30721-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="30721-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="30721-108">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="30721-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="30721-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém símbolos de locais do método.</span><span class="sxs-lookup"><span data-stu-id="30721-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30721-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="30721-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30721-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30721-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30721-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30721-112">Requirements</span></span>  
 <span data-ttu-id="30721-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30721-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30721-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30721-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30721-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30721-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30721-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30721-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30721-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30721-117">See also</span></span>

- [<span data-ttu-id="30721-118">Método GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="30721-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="30721-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="30721-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="30721-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="30721-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
