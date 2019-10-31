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
ms.openlocfilehash: 6de440d10f02f177e62ca3d2bd29fd5e98ea9388
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137138"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="3cfdf-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="3cfdf-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="3cfdf-103">Fornece notificação de eventos nativos que não estão diretamente relacionados ao Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3cfdf-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3cfdf-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3cfdf-104">Methods</span></span>  
  
|<span data-ttu-id="3cfdf-105">Método</span><span class="sxs-lookup"><span data-stu-id="3cfdf-105">Method</span></span>|<span data-ttu-id="3cfdf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cfdf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3cfdf-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="3cfdf-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="3cfdf-108">Notifica o depurador de que um evento nativo foi acionado.</span><span class="sxs-lookup"><span data-stu-id="3cfdf-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cfdf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cfdf-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cfdf-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="3cfdf-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cfdf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3cfdf-111">Requirements</span></span>  
 <span data-ttu-id="3cfdf-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cfdf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cfdf-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cfdf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cfdf-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cfdf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cfdf-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cfdf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cfdf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cfdf-116">See also</span></span>

- [<span data-ttu-id="3cfdf-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3cfdf-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
