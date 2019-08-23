---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936870"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="2422b-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="2422b-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="2422b-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="2422b-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2422b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2422b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2422b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2422b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="2422b-106">fora Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="2422b-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2422b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2422b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2422b-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2422b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2422b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2422b-109">Requirements</span></span>  
 <span data-ttu-id="2422b-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2422b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2422b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2422b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2422b-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2422b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2422b-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2422b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2422b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2422b-114">See also</span></span>

- [<span data-ttu-id="2422b-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="2422b-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="2422b-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2422b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
