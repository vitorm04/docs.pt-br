---
title: "Método ICorDebugMergedAssemblyRecord::GetIndex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ff8d6935f5507ab02d9d566921cb7f8a890bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="1bdd0-102">Método ICorDebugMergedAssemblyRecord::GetIndex</span><span class="sxs-lookup"><span data-stu-id="1bdd0-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="1bdd0-103">Obtém o índice do prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="1bdd0-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bdd0-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bdd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1bdd0-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="1bdd0-106">[out] Um ponteiro para o índice de prefixo.</span><span class="sxs-lookup"><span data-stu-id="1bdd0-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bdd0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bdd0-107">Remarks</span></span>  
 <span data-ttu-id="1bdd0-108">O índice de prefixo é usado para evitar colisões de nome nos nomes de tipo de metadados mesclada.</span><span class="sxs-lookup"><span data-stu-id="1bdd0-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bdd0-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1bdd0-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bdd0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1bdd0-110">Requirements</span></span>  
 <span data-ttu-id="1bdd0-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdd0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdd0-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bdd0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bdd0-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bdd0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bdd0-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdd0-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdd0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bdd0-115">See Also</span></span>  
 [<span data-ttu-id="1bdd0-116">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="1bdd0-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="1bdd0-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1bdd0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
