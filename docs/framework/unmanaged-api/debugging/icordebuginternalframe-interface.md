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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109818"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="21a48-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="21a48-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="21a48-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="21a48-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="21a48-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="21a48-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21a48-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="21a48-105">Methods</span></span>  
  
|<span data-ttu-id="21a48-106">Método</span><span class="sxs-lookup"><span data-stu-id="21a48-106">Method</span></span>|<span data-ttu-id="21a48-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="21a48-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21a48-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="21a48-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="21a48-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="21a48-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21a48-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="21a48-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a48-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="21a48-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a48-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21a48-112">Requirements</span></span>  
 <span data-ttu-id="21a48-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21a48-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a48-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21a48-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21a48-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21a48-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="21a48-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="21a48-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21a48-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21a48-117">See also</span></span>

- [<span data-ttu-id="21a48-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21a48-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
