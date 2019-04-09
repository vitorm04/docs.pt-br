---
title: Método ICorDebugSymbolProvider::GetStaticFieldSymbols
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bfab7a666a4c715b2236f5101bcceacb5b2fed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072682"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="2e58e-102">Método ICorDebugSymbolProvider::GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="2e58e-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="2e58e-103">Obtém os símbolos de campo estático que correspondem a uma assinatura de typespec.</span><span class="sxs-lookup"><span data-stu-id="2e58e-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e58e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e58e-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e58e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e58e-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="2e58e-106">[in] O número de bytes no `typeSig` matriz.</span><span class="sxs-lookup"><span data-stu-id="2e58e-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="2e58e-107">[in] Uma matriz de bytes que contém o `typespec` assinatura.</span><span class="sxs-lookup"><span data-stu-id="2e58e-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="2e58e-108">[in] O número de símbolos solicitado.</span><span class="sxs-lookup"><span data-stu-id="2e58e-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2e58e-109">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="2e58e-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="2e58e-110">[out] Um ponteiro para um [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) matriz que contém os símbolos de campo estático solicitado.</span><span class="sxs-lookup"><span data-stu-id="2e58e-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e58e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e58e-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e58e-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2e58e-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e58e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e58e-113">Requirements</span></span>  
 <span data-ttu-id="2e58e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e58e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e58e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e58e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e58e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e58e-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2e58e-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="2e58e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e58e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e58e-118">See also</span></span>

- [<span data-ttu-id="2e58e-119">Método GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="2e58e-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="2e58e-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="2e58e-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2e58e-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2e58e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
