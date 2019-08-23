---
title: Enumeração CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec23e0f272852088987fcc74767d3645778eab45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955678"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="08820-102">Enumeração CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="08820-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="08820-103">Fornece informações adicionais sobre eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="08820-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08820-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08820-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="08820-105">Membros</span><span class="sxs-lookup"><span data-stu-id="08820-105">Members</span></span>  
  
|<span data-ttu-id="08820-106">Membro</span><span class="sxs-lookup"><span data-stu-id="08820-106">Member</span></span>|<span data-ttu-id="08820-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="08820-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="08820-108">Indica que o evento de depuração é uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="08820-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08820-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="08820-109">Remarks</span></span>  
 <span data-ttu-id="08820-110">O método [ICorDebugProcess6::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) inclui um `dwFlags` parâmetro que fornece informações adicionais sobre um evento de depuração e cujo valor é dependente da arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="08820-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="08820-111">A enumeração `CorDebugDecodeEventFlagsWindows` pode ser usada com eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="08820-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08820-112">Essa enumeração destina-se ao uso em cenários de depuração .NET Native apenas.</span><span class="sxs-lookup"><span data-stu-id="08820-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08820-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08820-113">Requirements</span></span>  
 <span data-ttu-id="08820-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08820-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08820-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08820-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08820-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08820-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08820-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08820-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08820-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08820-118">See also</span></span>

- [<span data-ttu-id="08820-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="08820-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
