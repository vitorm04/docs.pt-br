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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993753"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="1de4b-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="1de4b-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="1de4b-103">Fornece notificação de eventos nativos que não estão diretamente relacionadas para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1de4b-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1de4b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1de4b-104">Methods</span></span>  
  
|<span data-ttu-id="1de4b-105">Método</span><span class="sxs-lookup"><span data-stu-id="1de4b-105">Method</span></span>|<span data-ttu-id="1de4b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1de4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1de4b-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="1de4b-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="1de4b-108">Notifica o depurador que um evento nativo foi disparado.</span><span class="sxs-lookup"><span data-stu-id="1de4b-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1de4b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1de4b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1de4b-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1de4b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de4b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1de4b-111">Requirements</span></span>  
 <span data-ttu-id="1de4b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1de4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1de4b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1de4b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1de4b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1de4b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1de4b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1de4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de4b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1de4b-116">See also</span></span>

- [<span data-ttu-id="1de4b-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1de4b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
