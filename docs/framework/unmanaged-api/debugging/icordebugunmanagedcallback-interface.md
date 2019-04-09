---
title: Interface ICorDebugUnmanagedCallback
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a1546068ae6a8c8be1c0af1ef3c7d770c23d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128668"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="8a719-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="8a719-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="8a719-103">Fornece notificação de eventos nativos que não estão diretamente relacionadas para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8a719-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a719-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8a719-104">Methods</span></span>  
  
|<span data-ttu-id="8a719-105">Método</span><span class="sxs-lookup"><span data-stu-id="8a719-105">Method</span></span>|<span data-ttu-id="8a719-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a719-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a719-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="8a719-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="8a719-108">Notifica o depurador que um evento nativo foi disparado.</span><span class="sxs-lookup"><span data-stu-id="8a719-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a719-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a719-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a719-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="8a719-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a719-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a719-111">Requirements</span></span>  
 <span data-ttu-id="8a719-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a719-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a719-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a719-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a719-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a719-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8a719-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8a719-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a719-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a719-116">See also</span></span>

- [<span data-ttu-id="8a719-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8a719-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
