---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183463"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="56cf3-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="56cf3-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="56cf3-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="56cf3-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56cf3-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56cf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56cf3-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="56cf3-106">[out] Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="56cf3-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56cf3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="56cf3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56cf3-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="56cf3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56cf3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56cf3-109">Requirements</span></span>  
 <span data-ttu-id="56cf3-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56cf3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56cf3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56cf3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56cf3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56cf3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="56cf3-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="56cf3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56cf3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56cf3-114">See also</span></span>

- [<span data-ttu-id="56cf3-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="56cf3-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="56cf3-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="56cf3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
