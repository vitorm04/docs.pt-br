---
title: Enumeração CorDebugHandleType
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6f5cd47abd4c17021bc324898a096ff70a3db2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739996"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="9cbdd-102">Enumeração CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="9cbdd-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="9cbdd-103">Indica o tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cbdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cbdd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="9cbdd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9cbdd-105">Members</span></span>  
  
|<span data-ttu-id="9cbdd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9cbdd-106">Member</span></span>|<span data-ttu-id="9cbdd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cbdd-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="9cbdd-108">O identificador será forte, o que impede que um objeto seja recuperada pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="9cbdd-109">O identificador é fraco, que não impede que um objeto seja recuperada pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="9cbdd-110">O identificador se torna inválido quando o objeto seja coletado.</span><span class="sxs-lookup"><span data-stu-id="9cbdd-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cbdd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cbdd-111">Requirements</span></span>  
 <span data-ttu-id="9cbdd-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cbdd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cbdd-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cbdd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cbdd-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cbdd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cbdd-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cbdd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbdd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cbdd-116">See also</span></span>

- [<span data-ttu-id="9cbdd-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9cbdd-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
