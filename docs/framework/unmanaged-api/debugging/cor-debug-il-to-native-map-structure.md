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
ms.openlocfilehash: 03ce77dd7407db8289abfefba13d71a9af053e10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609510"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="6b85c-102">Estrutura COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="6b85c-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="6b85c-103">Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="6b85c-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b85c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b85c-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="6b85c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6b85c-105">Members</span></span>  
  
|<span data-ttu-id="6b85c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6b85c-106">Member</span></span>|<span data-ttu-id="6b85c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b85c-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="6b85c-108">O deslocamento do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="6b85c-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="6b85c-109">O deslocamento do início do código nativo.</span><span class="sxs-lookup"><span data-stu-id="6b85c-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="6b85c-110">O deslocamento do final do código nativo.</span><span class="sxs-lookup"><span data-stu-id="6b85c-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b85c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b85c-111">Requirements</span></span>  
 <span data-ttu-id="6b85c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b85c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b85c-113">**Cabeçalho:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6b85c-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="6b85c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b85c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b85c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b85c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b85c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b85c-116">See also</span></span>

- [<span data-ttu-id="6b85c-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="6b85c-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="6b85c-118">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="6b85c-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="6b85c-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="6b85c-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6b85c-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="6b85c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
