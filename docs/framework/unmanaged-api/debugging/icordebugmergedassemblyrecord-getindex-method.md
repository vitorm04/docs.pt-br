---
title: Método ICorDebugMergedAssemblyRecord::GetIndex
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8ba470325098125aee8ef7de01fa6aa70596d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202593"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="754fc-102">Método ICorDebugMergedAssemblyRecord::GetIndex</span><span class="sxs-lookup"><span data-stu-id="754fc-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="754fc-103">Obtém o índice de prefixo do assembly.</span><span class="sxs-lookup"><span data-stu-id="754fc-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="754fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="754fc-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="754fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="754fc-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="754fc-106">[out] Um ponteiro para o índice de prefixo.</span><span class="sxs-lookup"><span data-stu-id="754fc-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="754fc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="754fc-107">Remarks</span></span>  
 <span data-ttu-id="754fc-108">O índice de prefixo é usado para evitar colisões de nome nos nomes de tipo de metadados mesclada.</span><span class="sxs-lookup"><span data-stu-id="754fc-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="754fc-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="754fc-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754fc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="754fc-110">Requirements</span></span>  
 <span data-ttu-id="754fc-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="754fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="754fc-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="754fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="754fc-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="754fc-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="754fc-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="754fc-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="754fc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="754fc-115">See also</span></span>

- [<span data-ttu-id="754fc-116">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="754fc-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="754fc-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="754fc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
