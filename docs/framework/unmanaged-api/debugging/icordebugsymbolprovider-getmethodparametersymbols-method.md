---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols Method
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be103b8f9d6f94d5b7a265ec2ef01c551622c9e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714289"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="4355d-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span><span class="sxs-lookup"><span data-stu-id="4355d-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="4355d-103">Obtém os símbolos de parâmetro do método dado o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="4355d-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4355d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4355d-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4355d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4355d-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="4355d-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="4355d-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="4355d-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="4355d-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4355d-108">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="4355d-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4355d-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém símbolos de locais do método.</span><span class="sxs-lookup"><span data-stu-id="4355d-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4355d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4355d-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4355d-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4355d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4355d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4355d-112">Requirements</span></span>  
 <span data-ttu-id="4355d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4355d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4355d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4355d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4355d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4355d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4355d-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4355d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4355d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4355d-117">See also</span></span>
- [<span data-ttu-id="4355d-118">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="4355d-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="4355d-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="4355d-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4355d-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4355d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
