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
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788651"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="8adcb-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="8adcb-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="8adcb-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8adcb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8adcb-104">Estende a interface de ICorDebugFunction logicamente para fornecer acesso ao código a partir de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="8adcb-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8adcb-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8adcb-105">Methods</span></span>  
  
|<span data-ttu-id="8adcb-106">Método</span><span class="sxs-lookup"><span data-stu-id="8adcb-106">Method</span></span>|<span data-ttu-id="8adcb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8adcb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8adcb-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="8adcb-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="8adcb-109">Obtém um ponteiro de interface para um [ICorDebugILCode](icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="8adcb-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8adcb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8adcb-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8adcb-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8adcb-111">Requirements</span></span>  
 <span data-ttu-id="8adcb-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adcb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adcb-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8adcb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8adcb-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8adcb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8adcb-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adcb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adcb-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="8adcb-116">See also</span></span>

- [<span data-ttu-id="8adcb-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8adcb-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8adcb-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="8adcb-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="8adcb-119">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="8adcb-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
