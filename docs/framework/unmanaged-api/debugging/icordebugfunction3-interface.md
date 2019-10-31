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
ms.openlocfilehash: fc50fd7180aaf5c1cff2147268d34921eec39e8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137759"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="93e26-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="93e26-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="93e26-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="93e26-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="93e26-104">Estende logicamente a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="93e26-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93e26-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="93e26-105">Methods</span></span>  
  
|<span data-ttu-id="93e26-106">Método</span><span class="sxs-lookup"><span data-stu-id="93e26-106">Method</span></span>|<span data-ttu-id="93e26-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="93e26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93e26-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="93e26-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="93e26-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="93e26-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93e26-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="93e26-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93e26-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93e26-111">Requirements</span></span>  
 <span data-ttu-id="93e26-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93e26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93e26-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93e26-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93e26-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93e26-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93e26-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93e26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e26-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93e26-116">See also</span></span>

- [<span data-ttu-id="93e26-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="93e26-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="93e26-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="93e26-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="93e26-119">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="93e26-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
