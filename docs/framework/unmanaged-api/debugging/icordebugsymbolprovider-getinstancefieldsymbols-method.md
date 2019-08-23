---
title: 'Método ICorDebugSymbolProvider:: GetInstanceFieldSymbols'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6bba47500b024bc1f2a2be21d461a6f5933f0ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964618"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="24f68-102">Método ICorDebugSymbolProvider:: GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="24f68-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="24f68-103">Obtém os símbolos de campo de instância que correspondem a uma assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="24f68-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24f68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24f68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24f68-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="24f68-106">no O número de bytes na `typeSig` matriz.</span><span class="sxs-lookup"><span data-stu-id="24f68-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="24f68-107">no Uma matriz de bytes que contém `typespec` a assinatura.</span><span class="sxs-lookup"><span data-stu-id="24f68-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="24f68-108">no O número de símbolos solicitados.</span><span class="sxs-lookup"><span data-stu-id="24f68-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="24f68-109">fora Um ponteiro para o número de símbolos recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="24f68-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="24f68-110">fora Um ponteiro para uma matriz [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) que contém os símbolos de campo de instância solicitados.</span><span class="sxs-lookup"><span data-stu-id="24f68-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24f68-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="24f68-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24f68-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="24f68-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f68-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24f68-113">Requirements</span></span>  
 <span data-ttu-id="24f68-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f68-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24f68-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f68-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f68-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f68-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f68-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24f68-118">See also</span></span>

- [<span data-ttu-id="24f68-119">Método GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="24f68-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="24f68-120">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="24f68-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="24f68-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="24f68-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
