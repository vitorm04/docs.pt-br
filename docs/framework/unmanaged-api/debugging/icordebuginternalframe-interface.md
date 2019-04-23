---
title: Interface ICorDebugInternalFrame
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f16b4628215bee2410708edeb337b41fbdc0311
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109818"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="7e22c-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="7e22c-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="7e22c-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="7e22c-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="7e22c-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="7e22c-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e22c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7e22c-105">Methods</span></span>  
  
|<span data-ttu-id="7e22c-106">Método</span><span class="sxs-lookup"><span data-stu-id="7e22c-106">Method</span></span>|<span data-ttu-id="7e22c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e22c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e22c-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="7e22c-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="7e22c-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="7e22c-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e22c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e22c-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e22c-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="7e22c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e22c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e22c-112">Requirements</span></span>  
 <span data-ttu-id="7e22c-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e22c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e22c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e22c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e22c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e22c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e22c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e22c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e22c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e22c-117">See also</span></span>

- [<span data-ttu-id="7e22c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7e22c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
