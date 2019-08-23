---
title: 'Método ICorDebugSymbolProvider:: GetStaticFieldSymbols'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd3442adf58250a423438666ec1092bab61958b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955549"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="58ed5-102">Método ICorDebugSymbolProvider:: GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="58ed5-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="58ed5-103">Obtém os símbolos de campo estático que correspondem a uma assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="58ed5-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ed5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58ed5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ed5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58ed5-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="58ed5-106">no O número de bytes na `typeSig` matriz.</span><span class="sxs-lookup"><span data-stu-id="58ed5-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="58ed5-107">no Uma matriz de bytes que contém `typespec` a assinatura.</span><span class="sxs-lookup"><span data-stu-id="58ed5-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="58ed5-108">no O número de símbolos solicitados.</span><span class="sxs-lookup"><span data-stu-id="58ed5-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="58ed5-109">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="58ed5-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="58ed5-110">fora Um ponteiro para uma matriz [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) que contém os símbolos de campo estáticos solicitados.</span><span class="sxs-lookup"><span data-stu-id="58ed5-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ed5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="58ed5-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58ed5-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="58ed5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ed5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58ed5-113">Requirements</span></span>  
 <span data-ttu-id="58ed5-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ed5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ed5-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ed5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ed5-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ed5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ed5-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ed5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ed5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58ed5-118">See also</span></span>

- [<span data-ttu-id="58ed5-119">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="58ed5-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="58ed5-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="58ed5-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="58ed5-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="58ed5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
