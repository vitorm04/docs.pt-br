---
title: Interface ICorDebugUnmanagedCallback
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa104bee5171b3b28731cf18a4d26e32f49169ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="37487-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="37487-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="37487-103">Fornece notificação de eventos nativo que não estão diretamente relacionados para o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="37487-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37487-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="37487-104">Methods</span></span>  
  
|<span data-ttu-id="37487-105">Método</span><span class="sxs-lookup"><span data-stu-id="37487-105">Method</span></span>|<span data-ttu-id="37487-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="37487-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37487-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="37487-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="37487-108">Notifica o depurador que um evento nativo foi acionado.</span><span class="sxs-lookup"><span data-stu-id="37487-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37487-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="37487-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37487-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="37487-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37487-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37487-111">Requirements</span></span>  
 <span data-ttu-id="37487-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37487-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37487-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37487-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37487-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37487-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37487-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37487-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37487-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37487-116">See Also</span></span>  
 [<span data-ttu-id="37487-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="37487-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
