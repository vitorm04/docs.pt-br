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
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964261"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="97b81-102">Interface ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="97b81-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="97b81-103">Fornece métodos que estendem os recursos do "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="97b81-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97b81-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="97b81-104">Methods</span></span>  
  
|<span data-ttu-id="97b81-105">Método</span><span class="sxs-lookup"><span data-stu-id="97b81-105">Method</span></span>|<span data-ttu-id="97b81-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="97b81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97b81-107">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="97b81-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="97b81-108">Obtém as partes do código que é composto por este objeto de código.</span><span class="sxs-lookup"><span data-stu-id="97b81-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="97b81-109">Método GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="97b81-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="97b81-110">Obtém os sinalizadores que especificam as condições sob as quais esse objeto de código foi o just-in-time (JIT) compilados ou gerados usando o gerador de imagem nativa (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="97b81-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97b81-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="97b81-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97b81-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="97b81-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b81-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97b81-113">Requirements</span></span>  
 <span data-ttu-id="97b81-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97b81-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97b81-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97b81-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97b81-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97b81-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97b81-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97b81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b81-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b81-118">See also</span></span>

- [<span data-ttu-id="97b81-119">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="97b81-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="97b81-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="97b81-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
