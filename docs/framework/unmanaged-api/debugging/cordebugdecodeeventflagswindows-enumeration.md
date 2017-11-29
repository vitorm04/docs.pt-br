---
title: "Enumeração CorDebugDecodeEventFlagsWindows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: facde76ec24d90795de7dfb70bfe5772a6f21531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="b4ccc-102">Enumeração CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="b4ccc-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="b4ccc-103">Fornece informações adicionais sobre eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="b4ccc-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ccc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4ccc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="b4ccc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b4ccc-105">Members</span></span>  
  
|<span data-ttu-id="b4ccc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b4ccc-106">Member</span></span>|<span data-ttu-id="b4ccc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4ccc-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="b4ccc-108">Indica que o evento de depuração é uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="b4ccc-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4ccc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4ccc-109">Remarks</span></span>  
 <span data-ttu-id="b4ccc-110">O [Icordebugprocess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) método inclui um `dwFlags` parâmetro que fornece informações adicionais sobre um evento de depuração e cujo valor é dependente da arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="b4ccc-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="b4ccc-111">A enumeração `CorDebugDecodeEventFlagsWindows` pode ser usada com eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="b4ccc-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4ccc-112">Essa enumeração é destinada ao uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="b4ccc-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ccc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4ccc-113">Requirements</span></span>  
 <span data-ttu-id="b4ccc-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ccc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ccc-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4ccc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4ccc-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ccc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ccc-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ccc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ccc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4ccc-118">See Also</span></span>  
 [<span data-ttu-id="b4ccc-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b4ccc-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
