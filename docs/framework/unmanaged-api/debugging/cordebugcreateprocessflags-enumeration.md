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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dfc7da632a5e56f0f6ab6ed55d1e722f49c7e88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740287"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="2e9b8-102">Enumeração CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="2e9b8-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="2e9b8-103">Fornece opções de depuração adicionais que podem ser usadas em uma chamada para o [icordebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2e9b8-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e9b8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2e9b8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2e9b8-105">Members</span></span>  
  
|<span data-ttu-id="2e9b8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2e9b8-106">Member</span></span>|<span data-ttu-id="2e9b8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e9b8-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="2e9b8-108">Sem opções especiais são definidas.</span><span class="sxs-lookup"><span data-stu-id="2e9b8-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e9b8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e9b8-109">Requirements</span></span>  
 <span data-ttu-id="2e9b8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e9b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9b8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e9b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e9b8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e9b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e9b8-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9b8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e9b8-114">See also</span></span>

- [<span data-ttu-id="2e9b8-115">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2e9b8-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
