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
ms.openlocfilehash: b74008e0a183d46d82c5262209d582537fd155c7
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938080"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="181fa-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="181fa-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="181fa-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="181fa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="181fa-104">Estende a interface de ICorDebugFunction logicamente para fornecer acesso ao código a partir de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="181fa-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="181fa-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="181fa-105">Methods</span></span>  
  
|<span data-ttu-id="181fa-106">Método</span><span class="sxs-lookup"><span data-stu-id="181fa-106">Method</span></span>|<span data-ttu-id="181fa-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="181fa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="181fa-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="181fa-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="181fa-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="181fa-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="181fa-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="181fa-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="181fa-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="181fa-111">Requirements</span></span>  
 <span data-ttu-id="181fa-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="181fa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="181fa-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="181fa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="181fa-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="181fa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="181fa-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="181fa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181fa-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="181fa-116">See also</span></span>

- [<span data-ttu-id="181fa-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="181fa-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="181fa-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="181fa-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="181fa-119">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="181fa-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
