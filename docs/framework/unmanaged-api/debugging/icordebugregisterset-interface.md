---
title: Interface ICorDebugRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792078"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="12033-102">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="12033-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="12033-103">Representa o conjunto de registros disponíveis no computador que está executando o código no momento.</span><span class="sxs-lookup"><span data-stu-id="12033-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12033-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="12033-104">Methods</span></span>  
  
|<span data-ttu-id="12033-105">Método</span><span class="sxs-lookup"><span data-stu-id="12033-105">Method</span></span>|<span data-ttu-id="12033-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="12033-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12033-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="12033-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="12033-108">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="12033-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="12033-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="12033-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="12033-110">Obtém uma máscara de bits que indica quais registros neste `ICorDebugRegisterSet` estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="12033-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="12033-111">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="12033-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="12033-112">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="12033-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="12033-113">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="12033-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="12033-114">Não implementado para a versão de .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="12033-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="12033-115">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="12033-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="12033-116">Não implementado para o .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="12033-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12033-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="12033-117">Remarks</span></span>  
 <span data-ttu-id="12033-118">A interface `ICorDebugRegisterSet` dá suporte apenas a registros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="12033-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="12033-119">Use a interface [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) em plataformas como IA-64 que exigem registros adicionais.</span><span class="sxs-lookup"><span data-stu-id="12033-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12033-120">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="12033-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12033-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="12033-121">Requirements</span></span>  
 <span data-ttu-id="12033-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12033-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12033-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12033-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12033-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12033-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12033-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12033-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12033-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="12033-126">See also</span></span>

- [<span data-ttu-id="12033-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="12033-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="12033-128">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="12033-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
