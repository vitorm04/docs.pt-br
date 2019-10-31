---
title: 'Método ICorDebugSymbolProvider:: GetStaticFieldSymbols'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 8c4211a60786016e25cc3e3419804817b57ab64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138799"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="73b1c-102">Método ICorDebugSymbolProvider:: GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="73b1c-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="73b1c-103">Obtém os símbolos de campo estático que correspondem a uma assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="73b1c-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73b1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73b1c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73b1c-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="73b1c-106">no O número de bytes na matriz de `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="73b1c-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="73b1c-107">no Uma matriz de bytes que contém a assinatura `typespec`.</span><span class="sxs-lookup"><span data-stu-id="73b1c-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="73b1c-108">no O número de símbolos solicitados.</span><span class="sxs-lookup"><span data-stu-id="73b1c-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="73b1c-109">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="73b1c-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="73b1c-110">fora Um ponteiro para uma matriz [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) que contém os símbolos de campo estáticos solicitados.</span><span class="sxs-lookup"><span data-stu-id="73b1c-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73b1c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="73b1c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73b1c-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="73b1c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73b1c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73b1c-113">Requirements</span></span>  
 <span data-ttu-id="73b1c-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73b1c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b1c-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73b1c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73b1c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73b1c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73b1c-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b1c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b1c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73b1c-118">See also</span></span>

- [<span data-ttu-id="73b1c-119">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="73b1c-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="73b1c-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="73b1c-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="73b1c-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="73b1c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
