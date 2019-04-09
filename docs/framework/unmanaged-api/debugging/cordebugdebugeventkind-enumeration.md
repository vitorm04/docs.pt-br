---
title: Enumeração CorDebugDebugEventKind
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e5479fad3f19c219a0ca1d5d01934ce92a7162e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127150"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="ab903-102">Enumeração CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="ab903-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="ab903-103">Indica o tipo de evento cujas informações são decodificadas pelo [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ab903-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab903-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab903-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="ab903-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ab903-105">Members</span></span>  
  
|<span data-ttu-id="ab903-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ab903-106">Member</span></span>|<span data-ttu-id="ab903-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab903-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="ab903-108">Um evento de carga do módulo.</span><span class="sxs-lookup"><span data-stu-id="ab903-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="ab903-109">Um evento de descarga do módulo.</span><span class="sxs-lookup"><span data-stu-id="ab903-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="ab903-110">Uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="ab903-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="ab903-111">Uma exceção de usuário de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="ab903-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="ab903-112">Uma exceção para a qual existe um manipulador `catch`.</span><span class="sxs-lookup"><span data-stu-id="ab903-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="ab903-113">Uma exceção não manipulada.</span><span class="sxs-lookup"><span data-stu-id="ab903-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab903-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab903-114">Remarks</span></span>  
 <span data-ttu-id="ab903-115">Um membro do `CorDebugDebugEventKind` enumeração é retornada ao chamar o [icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ab903-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab903-116">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="ab903-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab903-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab903-117">Requirements</span></span>  
 <span data-ttu-id="ab903-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab903-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab903-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab903-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab903-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab903-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ab903-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ab903-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab903-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab903-122">See also</span></span>

- [<span data-ttu-id="ab903-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="ab903-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
