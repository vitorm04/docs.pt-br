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
ms.openlocfilehash: 7f0570b668cc33ca509c8522d1ba35ebcfca2453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125583"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="62b93-102">Interface ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="62b93-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="62b93-103">Fornece métodos que estendem os recursos de "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="62b93-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62b93-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="62b93-104">Methods</span></span>  
  
|<span data-ttu-id="62b93-105">Método</span><span class="sxs-lookup"><span data-stu-id="62b93-105">Method</span></span>|<span data-ttu-id="62b93-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="62b93-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62b93-107">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="62b93-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="62b93-108">Obtém as partes de código das quais este objeto de código é composto.</span><span class="sxs-lookup"><span data-stu-id="62b93-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="62b93-109">Método GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="62b93-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="62b93-110">Obtém os sinalizadores que especificam as condições sob as quais esse objeto de código era JIT (just-in-time) compilado ou gerado usando o gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="62b93-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62b93-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="62b93-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62b93-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="62b93-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b93-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62b93-113">Requirements</span></span>  
 <span data-ttu-id="62b93-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b93-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b93-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62b93-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62b93-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b93-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b93-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b93-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b93-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62b93-118">See also</span></span>

- [<span data-ttu-id="62b93-119">Interface ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="62b93-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="62b93-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="62b93-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
