---
title: Estrutura COR_DEBUG_IL_TO_NATIVE_MAP
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56d4255b06f1317c87685737e4ee4021c37a77f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555005"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="6a336-102">Estrutura COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="6a336-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="6a336-103">Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="6a336-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a336-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a336-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="6a336-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6a336-105">Members</span></span>  
  
|<span data-ttu-id="6a336-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6a336-106">Member</span></span>|<span data-ttu-id="6a336-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a336-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="6a336-108">O deslocamento do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="6a336-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="6a336-109">O deslocamento do início do código nativo.</span><span class="sxs-lookup"><span data-stu-id="6a336-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="6a336-110">O deslocamento do final do código nativo.</span><span class="sxs-lookup"><span data-stu-id="6a336-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a336-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a336-111">Requirements</span></span>  
 <span data-ttu-id="6a336-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a336-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a336-113">**Cabeçalho:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6a336-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="6a336-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a336-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a336-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a336-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a336-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a336-116">See also</span></span>
- [<span data-ttu-id="6a336-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="6a336-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="6a336-118">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="6a336-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="6a336-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="6a336-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6a336-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="6a336-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
