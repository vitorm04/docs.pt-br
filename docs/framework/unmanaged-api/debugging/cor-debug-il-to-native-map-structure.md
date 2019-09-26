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
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274070"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="d121c-102">Estrutura COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="d121c-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="d121c-103">Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="d121c-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d121c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d121c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="d121c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d121c-105">Members</span></span>  
  
|<span data-ttu-id="d121c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d121c-106">Member</span></span>|<span data-ttu-id="d121c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d121c-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="d121c-108">O deslocamento do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="d121c-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="d121c-109">O deslocamento do início do código nativo.</span><span class="sxs-lookup"><span data-stu-id="d121c-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="d121c-110">O deslocamento do final do código nativo.</span><span class="sxs-lookup"><span data-stu-id="d121c-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d121c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d121c-111">Requirements</span></span>  
 <span data-ttu-id="d121c-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d121c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d121c-113">**Cabeçalho:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d121c-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="d121c-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d121c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d121c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d121c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d121c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d121c-116">See also</span></span>

- [<span data-ttu-id="d121c-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="d121c-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="d121c-118">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="d121c-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="d121c-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d121c-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d121c-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="d121c-120">Debugging</span></span>](index.md)
