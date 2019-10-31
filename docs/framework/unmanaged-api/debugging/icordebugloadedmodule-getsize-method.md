---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122641"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="98e9f-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="98e9f-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="98e9f-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="98e9f-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e9f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98e9f-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="98e9f-106">fora Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="98e9f-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e9f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="98e9f-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98e9f-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="98e9f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e9f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98e9f-109">Requirements</span></span>  
 <span data-ttu-id="98e9f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e9f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98e9f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e9f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e9f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e9f-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e9f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e9f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98e9f-114">See also</span></span>

- [<span data-ttu-id="98e9f-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="98e9f-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="98e9f-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="98e9f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
