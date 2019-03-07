---
title: Método ICorDebugInstanceFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2119b1ce43d5969c8d083e955210c69af69b44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491427"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="d85dc-102">Método ICorDebugInstanceFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="d85dc-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="d85dc-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="d85dc-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d85dc-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d85dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d85dc-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="d85dc-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="d85dc-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85dc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d85dc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d85dc-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d85dc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85dc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d85dc-109">Requirements</span></span>  
 <span data-ttu-id="d85dc-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d85dc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d85dc-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d85dc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d85dc-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d85dc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d85dc-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d85dc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85dc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d85dc-114">See also</span></span>
- [<span data-ttu-id="d85dc-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="d85dc-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="d85dc-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d85dc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
