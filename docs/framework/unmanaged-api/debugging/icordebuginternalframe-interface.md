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
ms.openlocfilehash: 6a1af92cbce84b674058ab2c8af2e15b0070dcd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974751"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="a8224-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="a8224-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="a8224-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="a8224-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="a8224-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a8224-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8224-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a8224-105">Methods</span></span>  
  
|<span data-ttu-id="a8224-106">Método</span><span class="sxs-lookup"><span data-stu-id="a8224-106">Method</span></span>|<span data-ttu-id="a8224-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8224-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8224-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="a8224-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="a8224-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="a8224-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8224-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8224-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8224-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a8224-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8224-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8224-112">Requirements</span></span>  
 <span data-ttu-id="a8224-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8224-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8224-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8224-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8224-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8224-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8224-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8224-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8224-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8224-117">See also</span></span>
- [<span data-ttu-id="a8224-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a8224-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
