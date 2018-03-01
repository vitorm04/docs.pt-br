---
title: ICorDebugInternalFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e950847764e695f705aeded0e3804db4b872827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="b53f2-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="b53f2-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="b53f2-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="b53f2-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="b53f2-104">Esta interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b53f2-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b53f2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b53f2-105">Methods</span></span>  
  
|<span data-ttu-id="b53f2-106">Método</span><span class="sxs-lookup"><span data-stu-id="b53f2-106">Method</span></span>|<span data-ttu-id="b53f2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b53f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b53f2-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="b53f2-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="b53f2-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="b53f2-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b53f2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b53f2-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b53f2-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="b53f2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53f2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b53f2-112">Requirements</span></span>  
 <span data-ttu-id="b53f2-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53f2-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b53f2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b53f2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b53f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b53f2-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53f2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b53f2-117">See Also</span></span>  
 [<span data-ttu-id="b53f2-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b53f2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
