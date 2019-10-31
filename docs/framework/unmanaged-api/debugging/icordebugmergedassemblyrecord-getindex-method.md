---
title: 'Método ICorDebugMergedAssemblyRecord:: GetIndex'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: 236bd8b22d6c3ec783d787f6c906ede3193cfc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131401"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="01161-102">Método ICorDebugMergedAssemblyRecord:: GetIndex</span><span class="sxs-lookup"><span data-stu-id="01161-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="01161-103">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="01161-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01161-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01161-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01161-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01161-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="01161-106">fora Um ponteiro para o índice de prefixo.</span><span class="sxs-lookup"><span data-stu-id="01161-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01161-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="01161-107">Remarks</span></span>  
 <span data-ttu-id="01161-108">O índice de prefixo é usado para evitar colisões de nome nos nomes de tipos de metadados mesclados.</span><span class="sxs-lookup"><span data-stu-id="01161-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01161-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01161-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01161-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01161-110">Requirements</span></span>  
 <span data-ttu-id="01161-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01161-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01161-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01161-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01161-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01161-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01161-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01161-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01161-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01161-115">See also</span></span>

- [<span data-ttu-id="01161-116">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="01161-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="01161-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="01161-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
