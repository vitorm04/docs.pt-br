---
title: ICorDebugInternalFrame Interface1
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
ms.openlocfilehash: 45a710e6d8be4a041d9852585ea83fea85376f66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413820"
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="161cd-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="161cd-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="161cd-103">Representa um quadro de tempo de execução interno na pilha.</span><span class="sxs-lookup"><span data-stu-id="161cd-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="161cd-104">Esta interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="161cd-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="161cd-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="161cd-105">Methods</span></span>  
  
|<span data-ttu-id="161cd-106">Método</span><span class="sxs-lookup"><span data-stu-id="161cd-106">Method</span></span>|<span data-ttu-id="161cd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="161cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="161cd-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="161cd-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="161cd-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="161cd-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="161cd-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="161cd-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="161cd-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="161cd-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161cd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="161cd-112">Requirements</span></span>  
 <span data-ttu-id="161cd-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161cd-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="161cd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="161cd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="161cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="161cd-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161cd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="161cd-117">See Also</span></span>  
 [<span data-ttu-id="161cd-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="161cd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
