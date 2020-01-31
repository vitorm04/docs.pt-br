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
ms.openlocfilehash: fdd2fee11e9353c3aa3faee2b137597e4ba47801
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791178"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="efd94-102">Interface ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="efd94-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="efd94-103">Fornece notificação de eventos nativos que não estão diretamente relacionados ao Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="efd94-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efd94-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="efd94-104">Methods</span></span>  
  
|<span data-ttu-id="efd94-105">Método</span><span class="sxs-lookup"><span data-stu-id="efd94-105">Method</span></span>|<span data-ttu-id="efd94-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="efd94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efd94-107">Método DebugEvent</span><span class="sxs-lookup"><span data-stu-id="efd94-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="efd94-108">Notifica o depurador de que um evento nativo foi acionado.</span><span class="sxs-lookup"><span data-stu-id="efd94-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efd94-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="efd94-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efd94-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="efd94-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd94-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="efd94-111">Requirements</span></span>  
 <span data-ttu-id="efd94-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd94-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efd94-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efd94-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efd94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efd94-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd94-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="efd94-116">See also</span></span>

- [<span data-ttu-id="efd94-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="efd94-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
