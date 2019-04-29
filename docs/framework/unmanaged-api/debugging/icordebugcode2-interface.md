---
title: Interface ICorDebugCode2
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750105"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="6ade8-102">Interface ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="6ade8-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="6ade8-103">Fornece métodos que estendem os recursos do "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="6ade8-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ade8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6ade8-104">Methods</span></span>  
  
|<span data-ttu-id="6ade8-105">Método</span><span class="sxs-lookup"><span data-stu-id="6ade8-105">Method</span></span>|<span data-ttu-id="6ade8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ade8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ade8-107">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="6ade8-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="6ade8-108">Obtém as partes do código que é composto por este objeto de código.</span><span class="sxs-lookup"><span data-stu-id="6ade8-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="6ade8-109">Método GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="6ade8-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="6ade8-110">Obtém os sinalizadores que especificam as condições sob as quais esse objeto de código foi o just-in-time (JIT) compilados ou gerados usando o gerador de imagem nativa (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="6ade8-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ade8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ade8-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ade8-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="6ade8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ade8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ade8-113">Requirements</span></span>  
 <span data-ttu-id="6ade8-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ade8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ade8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ade8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ade8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ade8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ade8-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ade8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ade8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ade8-118">See also</span></span>

- [<span data-ttu-id="6ade8-119">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="6ade8-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="6ade8-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6ade8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
