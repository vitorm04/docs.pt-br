---
title: Interface ICorDebugILFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4f57f27ec92e7977b46ebfa5967b0590674d2a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113432"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="f3058-102">Interface ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="f3058-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="f3058-103">Uma extensão lógica da interface ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="f3058-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3058-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f3058-104">Methods</span></span>  
  
|<span data-ttu-id="f3058-105">Método</span><span class="sxs-lookup"><span data-stu-id="f3058-105">Method</span></span>|<span data-ttu-id="f3058-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3058-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3058-107">Método EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="f3058-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="f3058-108">Obtém um objeto ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros neste quadro.</span><span class="sxs-lookup"><span data-stu-id="f3058-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="f3058-109">Método RemapFunction</span><span class="sxs-lookup"><span data-stu-id="f3058-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="f3058-110">Remapeia uma função editada, especificando o novo deslocamento do MSIL.</span><span class="sxs-lookup"><span data-stu-id="f3058-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3058-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3058-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3058-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="f3058-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3058-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3058-113">Requirements</span></span>  
 <span data-ttu-id="f3058-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3058-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3058-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3058-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3058-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3058-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3058-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3058-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3058-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3058-118">See also</span></span>

- [<span data-ttu-id="f3058-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f3058-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
