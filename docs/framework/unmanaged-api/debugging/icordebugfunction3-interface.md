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
ms.openlocfilehash: c1945e678dd62f81c698807714d0e71053d6b378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414779"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="2c7e3-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="2c7e3-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="2c7e3-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2c7e3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2c7e3-104">Logicamente estende a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2c7e3-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c7e3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c7e3-105">Methods</span></span>  
  
|<span data-ttu-id="2c7e3-106">Método</span><span class="sxs-lookup"><span data-stu-id="2c7e3-106">Method</span></span>|<span data-ttu-id="2c7e3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c7e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c7e3-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="2c7e3-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="2c7e3-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="2c7e3-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c7e3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c7e3-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c7e3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c7e3-111">Requirements</span></span>  
 <span data-ttu-id="2c7e3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c7e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c7e3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c7e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c7e3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c7e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c7e3-115">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c7e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7e3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c7e3-116">See Also</span></span>  
 [<span data-ttu-id="2c7e3-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c7e3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2c7e3-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="2c7e3-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="2c7e3-119">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="2c7e3-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
