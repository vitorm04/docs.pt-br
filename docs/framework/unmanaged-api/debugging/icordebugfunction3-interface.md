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
ms.openlocfilehash: 71aa482cc2268da17f1376d8c305dd6a818d92d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213160"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="2c558-102">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="2c558-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="2c558-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2c558-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2c558-104">Estende a interface de ICorDebugFunction logicamente para fornecer acesso ao código a partir de uma solicitação ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2c558-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c558-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c558-105">Methods</span></span>  
  
|<span data-ttu-id="2c558-106">Método</span><span class="sxs-lookup"><span data-stu-id="2c558-106">Method</span></span>|<span data-ttu-id="2c558-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c558-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c558-108">Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="2c558-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="2c558-109">Obtém um ponteiro de interface para um [ICorDebugILCode](icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="2c558-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c558-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c558-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c558-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c558-111">Requirements</span></span>  
 <span data-ttu-id="2c558-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c558-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c558-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c558-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c558-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c558-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c558-115">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c558-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c558-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c558-116">See also</span></span>

- [<span data-ttu-id="2c558-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c558-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2c558-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="2c558-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="2c558-119">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="2c558-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
