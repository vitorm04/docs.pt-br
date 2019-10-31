---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 8af814ff2eaaf3ae6dae9031c13bf37ea0c1236b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122651"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="502df-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="502df-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="502df-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="502df-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="502df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="502df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="502df-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="502df-106">fora Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="502df-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="502df-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="502df-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="502df-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="502df-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="502df-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="502df-109">Requirements</span></span>  
 <span data-ttu-id="502df-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="502df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="502df-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="502df-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="502df-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="502df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="502df-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="502df-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502df-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="502df-114">See also</span></span>

- [<span data-ttu-id="502df-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="502df-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="502df-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="502df-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
