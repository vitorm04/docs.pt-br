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
ms.openlocfilehash: a34454e7e007b4eba557c712cb824362aa5047c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952985"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="04d13-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="04d13-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="04d13-103">Fornece notificação de eventos nativos que não estão diretamente relacionados ao Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="04d13-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04d13-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="04d13-104">Methods</span></span>  
  
|<span data-ttu-id="04d13-105">Método</span><span class="sxs-lookup"><span data-stu-id="04d13-105">Method</span></span>|<span data-ttu-id="04d13-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04d13-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="04d13-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="04d13-108">Notifica o depurador de que um evento nativo foi acionado.</span><span class="sxs-lookup"><span data-stu-id="04d13-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04d13-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="04d13-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04d13-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="04d13-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d13-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04d13-111">Requirements</span></span>  
 <span data-ttu-id="04d13-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d13-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d13-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04d13-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04d13-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04d13-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04d13-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d13-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04d13-116">See also</span></span>

- [<span data-ttu-id="04d13-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="04d13-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
