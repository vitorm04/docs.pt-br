---
title: Interface ICorDebugModuleBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6a43a264fcaa94ce4e629d8db504e9d416f6b89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179706"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="43059-102">Interface ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="43059-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="43059-103">Fornece acesso aos módulos específicos.</span><span class="sxs-lookup"><span data-stu-id="43059-103">Provides access to specific modules.</span></span> <span data-ttu-id="43059-104">Essa interface é uma subclasse da interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="43059-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43059-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="43059-105">Methods</span></span>  
  
|<span data-ttu-id="43059-106">Método</span><span class="sxs-lookup"><span data-stu-id="43059-106">Method</span></span>|<span data-ttu-id="43059-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="43059-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43059-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="43059-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="43059-109">Obtém um ponteiro de interface para um ICorDebugModule que faz referência ao módulo em que este ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="43059-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43059-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="43059-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43059-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="43059-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43059-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43059-112">Requirements</span></span>  
 <span data-ttu-id="43059-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43059-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43059-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43059-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43059-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43059-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="43059-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="43059-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43059-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43059-117">See also</span></span>

- [<span data-ttu-id="43059-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="43059-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
