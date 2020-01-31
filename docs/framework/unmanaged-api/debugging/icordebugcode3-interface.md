---
title: Interface ICorDebugCode3
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777824"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="04592-102">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="04592-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="04592-103">Fornece um método que estende "ICorDebugCode" e "ICorDebugCode2" para fornecer informações sobre um valor de retorno gerenciado.</span><span class="sxs-lookup"><span data-stu-id="04592-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04592-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="04592-104">Methods</span></span>  
  
|<span data-ttu-id="04592-105">Método</span><span class="sxs-lookup"><span data-stu-id="04592-105">Method</span></span>|<span data-ttu-id="04592-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="04592-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04592-107">Método GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="04592-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="04592-108">Para um deslocamento de IL especificado, obtém os deslocamentos nativos onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="04592-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04592-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="04592-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04592-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="04592-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04592-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="04592-111">Requirements</span></span>  
 <span data-ttu-id="04592-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04592-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04592-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04592-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04592-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04592-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04592-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04592-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04592-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="04592-116">See also</span></span>

- [<span data-ttu-id="04592-117">Interface ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="04592-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="04592-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="04592-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
