---
title: Método ICorDebugSymbolProvider::GetInstanceFieldSymbols
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d149eeec545909d9d6b7413c7ad6d537c1493bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501312"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="da501-102">Método ICorDebugSymbolProvider::GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="da501-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="da501-103">Obtém a instância de símbolos de campo que correspondem a uma assinatura de typespec.</span><span class="sxs-lookup"><span data-stu-id="da501-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da501-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da501-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da501-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da501-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="da501-106">[in] O número de bytes no `typeSig` matriz.</span><span class="sxs-lookup"><span data-stu-id="da501-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="da501-107">[in] Uma matriz de bytes que contém o `typespec` assinatura.</span><span class="sxs-lookup"><span data-stu-id="da501-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="da501-108">[in] O número de símbolos solicitado.</span><span class="sxs-lookup"><span data-stu-id="da501-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="da501-109">[out] Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="da501-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="da501-110">[out] Um ponteiro para um [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) matriz que contém os símbolos de campo de instância solicitada.</span><span class="sxs-lookup"><span data-stu-id="da501-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da501-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="da501-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da501-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da501-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da501-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da501-113">Requirements</span></span>  
 <span data-ttu-id="da501-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da501-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da501-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da501-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da501-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da501-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da501-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da501-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da501-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da501-118">See also</span></span>
- [<span data-ttu-id="da501-119">Método GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="da501-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="da501-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="da501-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="da501-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="da501-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
