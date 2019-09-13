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
ms.openlocfilehash: a3eebdf56796fe599ec6ff62d7008d1af3be796e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926833"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="f7e3c-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="f7e3c-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="f7e3c-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="f7e3c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f7e3c-104">Estende logicamente a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f7e3c-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7e3c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f7e3c-105">Methods</span></span>  
  
|<span data-ttu-id="f7e3c-106">Método</span><span class="sxs-lookup"><span data-stu-id="f7e3c-106">Method</span></span>|<span data-ttu-id="f7e3c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7e3c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7e3c-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="f7e3c-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="f7e3c-109">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="f7e3c-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7e3c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7e3c-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e3c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7e3c-111">Requirements</span></span>  
 <span data-ttu-id="f7e3c-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e3c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7e3c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7e3c-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7e3c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e3c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e3c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7e3c-116">See also</span></span>

- [<span data-ttu-id="f7e3c-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f7e3c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7e3c-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="f7e3c-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f7e3c-119">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="f7e3c-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
