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
ms.openlocfilehash: fd61c8133d9f155ae8e15bbc6aa90b2b9de1aadd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647655"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="39bd9-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="39bd9-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="39bd9-103">Fornece notificação de eventos nativos que não estão diretamente relacionadas para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="39bd9-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39bd9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="39bd9-104">Methods</span></span>  
  
|<span data-ttu-id="39bd9-105">Método</span><span class="sxs-lookup"><span data-stu-id="39bd9-105">Method</span></span>|<span data-ttu-id="39bd9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="39bd9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39bd9-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="39bd9-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="39bd9-108">Notifica o depurador que um evento nativo foi disparado.</span><span class="sxs-lookup"><span data-stu-id="39bd9-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39bd9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="39bd9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39bd9-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="39bd9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39bd9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39bd9-111">Requirements</span></span>  
 <span data-ttu-id="39bd9-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39bd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bd9-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39bd9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39bd9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39bd9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39bd9-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39bd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bd9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39bd9-116">See also</span></span>
- [<span data-ttu-id="39bd9-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="39bd9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
