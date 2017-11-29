---
title: "Enumeração CorDebugCreateProcessFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35503a89077b05d622ccc3f8e5cf1bb7d95ea9e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="9848d-102">Enumeração CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="9848d-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="9848d-103">Fornece opções adicionais de depuração que podem ser usadas em uma chamada para o [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="9848d-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9848d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9848d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9848d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9848d-105">Members</span></span>  
  
|<span data-ttu-id="9848d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9848d-106">Member</span></span>|<span data-ttu-id="9848d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9848d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="9848d-108">Sem opções especiais são definidas.</span><span class="sxs-lookup"><span data-stu-id="9848d-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9848d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9848d-109">Requirements</span></span>  
 <span data-ttu-id="9848d-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9848d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9848d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9848d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9848d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9848d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9848d-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9848d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9848d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9848d-114">See Also</span></span>  
 [<span data-ttu-id="9848d-115">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9848d-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
