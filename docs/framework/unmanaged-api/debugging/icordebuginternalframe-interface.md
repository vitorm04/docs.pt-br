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
ms.openlocfilehash: 6bc24450cdda2e3ed324256b53b2d137d1eb90e4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788491"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="74310-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="74310-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="74310-103">Representa um quadro interno de tempo de execução na pilha.</span><span class="sxs-lookup"><span data-stu-id="74310-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="74310-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="74310-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74310-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="74310-105">Methods</span></span>  
  
|<span data-ttu-id="74310-106">Método</span><span class="sxs-lookup"><span data-stu-id="74310-106">Method</span></span>|<span data-ttu-id="74310-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="74310-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74310-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="74310-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="74310-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="74310-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74310-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="74310-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74310-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="74310-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74310-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="74310-112">Requirements</span></span>  
 <span data-ttu-id="74310-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74310-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74310-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74310-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74310-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74310-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74310-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74310-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74310-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="74310-117">See also</span></span>

- [<span data-ttu-id="74310-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74310-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
