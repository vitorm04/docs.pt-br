---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce937b28d705fc35165368fa81a376facce18a30
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476497"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="f6f76-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="f6f76-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="f6f76-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f6f76-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6f76-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6f76-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6f76-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f6f76-106">[out] Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f6f76-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6f76-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6f76-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6f76-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f6f76-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f76-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6f76-109">Requirements</span></span>  
 <span data-ttu-id="f6f76-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6f76-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f76-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6f76-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6f76-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6f76-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6f76-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6f76-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f76-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6f76-114">See also</span></span>
- [<span data-ttu-id="f6f76-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="f6f76-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f6f76-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f6f76-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
