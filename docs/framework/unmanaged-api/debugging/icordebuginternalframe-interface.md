---
title: ICorDebugInternalFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame
helpviewer_keywords: ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a05ba891e734fbf5a94b2a1f91e29d484e1c788b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="7a9d1-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="7a9d1-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="7a9d1-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="7a9d1-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="7a9d1-104">Esta interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="7a9d1-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a9d1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7a9d1-105">Methods</span></span>  
  
|<span data-ttu-id="7a9d1-106">Método</span><span class="sxs-lookup"><span data-stu-id="7a9d1-106">Method</span></span>|<span data-ttu-id="7a9d1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a9d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a9d1-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="7a9d1-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="7a9d1-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="7a9d1-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a9d1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a9d1-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a9d1-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="7a9d1-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a9d1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a9d1-112">Requirements</span></span>  
 <span data-ttu-id="7a9d1-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a9d1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a9d1-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a9d1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a9d1-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a9d1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a9d1-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a9d1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9d1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a9d1-117">See Also</span></span>  
 [<span data-ttu-id="7a9d1-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7a9d1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
