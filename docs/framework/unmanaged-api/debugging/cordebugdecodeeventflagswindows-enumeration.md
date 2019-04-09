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
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207728"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="642b7-102">Enumeração CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="642b7-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="642b7-103">Fornece informações adicionais sobre eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="642b7-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="642b7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="642b7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="642b7-105">Members</span></span>  
  
|<span data-ttu-id="642b7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="642b7-106">Member</span></span>|<span data-ttu-id="642b7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="642b7-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="642b7-108">Indica que o evento de depuração é uma exceção de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="642b7-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642b7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="642b7-109">Remarks</span></span>  
 <span data-ttu-id="642b7-110">O [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) método inclui um `dwFlags` parâmetro que fornece informações adicionais sobre um evento de depuração e cujo valor é dependente da arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="642b7-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="642b7-111">A enumeração `CorDebugDecodeEventFlagsWindows` pode ser usada com eventos de depuração na plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="642b7-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="642b7-112">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="642b7-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642b7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="642b7-113">Requirements</span></span>  
 <span data-ttu-id="642b7-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="642b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="642b7-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="642b7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="642b7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="642b7-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="642b7-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="642b7-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="642b7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="642b7-118">See also</span></span>

- [<span data-ttu-id="642b7-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="642b7-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
