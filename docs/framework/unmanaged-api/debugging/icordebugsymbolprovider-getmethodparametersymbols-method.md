---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols Method
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98efd1446c88c3a6c004b5a3254c9db835a43804
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197367"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="04ffa-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span><span class="sxs-lookup"><span data-stu-id="04ffa-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="04ffa-103">Obtém os símbolos de parâmetro do método dado o endereço virtual relativo (RVA) desse método.</span><span class="sxs-lookup"><span data-stu-id="04ffa-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ffa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04ffa-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ffa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04ffa-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="04ffa-106">[in] O endereço de virtual relativo nativo do método.</span><span class="sxs-lookup"><span data-stu-id="04ffa-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="04ffa-107">[in] O número de símbolos locais solicitado.</span><span class="sxs-lookup"><span data-stu-id="04ffa-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="04ffa-108">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="04ffa-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="04ffa-109">[out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém símbolos de locais do método.</span><span class="sxs-lookup"><span data-stu-id="04ffa-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ffa-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="04ffa-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ffa-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04ffa-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ffa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04ffa-112">Requirements</span></span>  
 <span data-ttu-id="04ffa-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ffa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ffa-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04ffa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ffa-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ffa-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="04ffa-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="04ffa-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="04ffa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04ffa-117">See also</span></span>

- [<span data-ttu-id="04ffa-118">Método GetMethodLocalSymbols</span><span class="sxs-lookup"><span data-stu-id="04ffa-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="04ffa-119">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="04ffa-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="04ffa-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="04ffa-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
