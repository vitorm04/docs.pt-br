---
title: Enumeração CorDebugCreateProcessFlags
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: d28f6eab5390194a4089cbbaf1f586c3f53a7db5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132249"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="c88ad-102">Enumeração CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="c88ad-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="c88ad-103">Fornece opções de depuração adicionais que podem ser usadas em uma chamada para o método [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c88ad-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c88ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c88ad-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c88ad-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c88ad-105">Members</span></span>  
  
|<span data-ttu-id="c88ad-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c88ad-106">Member</span></span>|<span data-ttu-id="c88ad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c88ad-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="c88ad-108">Não há opções especiais definidas.</span><span class="sxs-lookup"><span data-stu-id="c88ad-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c88ad-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c88ad-109">Requirements</span></span>  
 <span data-ttu-id="c88ad-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c88ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c88ad-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c88ad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c88ad-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c88ad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c88ad-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c88ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88ad-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c88ad-114">See also</span></span>

- [<span data-ttu-id="c88ad-115">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="c88ad-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
