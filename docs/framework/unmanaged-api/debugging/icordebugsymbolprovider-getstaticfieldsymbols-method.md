---
title: "Método ICorDebugSymbolProvider::GetStaticFieldSymbols"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3871a74ee2844835c09a6e395fd63536c7442261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="d577f-102">Método ICorDebugSymbolProvider::GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="d577f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="d577f-103">Obtém os símbolos de campo estático que correspondem a uma assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="d577f-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d577f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d577f-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d577f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d577f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="d577f-106">[in] O número de bytes a `typeSig` matriz.</span><span class="sxs-lookup"><span data-stu-id="d577f-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="d577f-107">[in] Uma matriz de bytes que contém o `typespec` assinatura.</span><span class="sxs-lookup"><span data-stu-id="d577f-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="d577f-108">[in] O número de símbolos solicitado.</span><span class="sxs-lookup"><span data-stu-id="d577f-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="d577f-109">[out] Um ponteiro para o número de símbolos recuperada pelo método.</span><span class="sxs-lookup"><span data-stu-id="d577f-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="d577f-110">[out] Um ponteiro para um [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) matriz que contém os símbolos de campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="d577f-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d577f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d577f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d577f-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d577f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d577f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d577f-113">Requirements</span></span>  
 <span data-ttu-id="d577f-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d577f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d577f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d577f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d577f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d577f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d577f-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d577f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d577f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d577f-118">See Also</span></span>  
 [<span data-ttu-id="d577f-119">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="d577f-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="d577f-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="d577f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="d577f-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d577f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
