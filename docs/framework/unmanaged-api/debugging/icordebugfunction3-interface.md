---
title: Interface ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff49d64b0b58d301d24e39bc626abf6520c031b9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514213"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="9b363-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="9b363-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="9b363-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="9b363-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9b363-104">Estende logicamente a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="9b363-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b363-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9b363-105">Methods</span></span>  
  
|<span data-ttu-id="9b363-106">Método</span><span class="sxs-lookup"><span data-stu-id="9b363-106">Method</span></span>|<span data-ttu-id="9b363-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b363-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b363-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="9b363-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="9b363-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="9b363-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b363-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b363-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b363-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b363-111">Requirements</span></span>  
 <span data-ttu-id="9b363-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b363-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b363-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b363-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b363-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b363-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b363-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b363-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b363-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b363-116">See Also</span></span>  
 [<span data-ttu-id="9b363-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9b363-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9b363-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="9b363-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="9b363-119">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="9b363-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
