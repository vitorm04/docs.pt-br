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
ms.openlocfilehash: b7db7c9e17d87b91e09d5d010d40431cba5385df
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795983"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="78cf3-102">Enumeração CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="78cf3-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="78cf3-103">Indica o tipo de evento cujas informações são decodificadas pelo método [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="78cf3-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78cf3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="78cf3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="78cf3-105">Members</span></span>  
  
|<span data-ttu-id="78cf3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="78cf3-106">Member</span></span>|<span data-ttu-id="78cf3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="78cf3-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="78cf3-108">Um evento de carga do módulo.</span><span class="sxs-lookup"><span data-stu-id="78cf3-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="78cf3-109">Um evento de descarga do módulo.</span><span class="sxs-lookup"><span data-stu-id="78cf3-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="78cf3-110">Uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="78cf3-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="78cf3-111">Uma exceção de usuário de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="78cf3-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="78cf3-112">Uma exceção para a qual existe um manipulador `catch`.</span><span class="sxs-lookup"><span data-stu-id="78cf3-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="78cf3-113">Uma exceção não manipulada.</span><span class="sxs-lookup"><span data-stu-id="78cf3-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78cf3-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="78cf3-114">Remarks</span></span>  
 <span data-ttu-id="78cf3-115">Um membro da `CorDebugDebugEventKind` enumeração é retornado chamando o método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="78cf3-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78cf3-116">Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.</span><span class="sxs-lookup"><span data-stu-id="78cf3-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cf3-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78cf3-117">Requirements</span></span>  
 <span data-ttu-id="78cf3-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cf3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cf3-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78cf3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78cf3-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78cf3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78cf3-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cf3-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cf3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78cf3-122">See also</span></span>

- [<span data-ttu-id="78cf3-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="78cf3-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
