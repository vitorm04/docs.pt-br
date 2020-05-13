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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378264"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="4cd08-102">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="4cd08-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="4cd08-103">Representa o conjunto de registros disponíveis no computador que está executando o código no momento.</span><span class="sxs-lookup"><span data-stu-id="4cd08-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cd08-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4cd08-104">Methods</span></span>  
  
|<span data-ttu-id="4cd08-105">Método</span><span class="sxs-lookup"><span data-stu-id="4cd08-105">Method</span></span>|<span data-ttu-id="4cd08-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4cd08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cd08-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="4cd08-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="4cd08-108">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="4cd08-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="4cd08-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="4cd08-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="4cd08-110">Obtém uma máscara de bits que indica quais registros `ICorDebugRegisterSet` estão disponíveis no momento.</span><span class="sxs-lookup"><span data-stu-id="4cd08-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="4cd08-111">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4cd08-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="4cd08-112">Obtém o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="4cd08-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="4cd08-113">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="4cd08-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="4cd08-114">Não implementado para a versão de .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4cd08-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="4cd08-115">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4cd08-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="4cd08-116">Não implementado para o .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4cd08-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cd08-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4cd08-117">Remarks</span></span>  
 <span data-ttu-id="4cd08-118">A `ICorDebugRegisterSet` interface dá suporte apenas a registros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="4cd08-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="4cd08-119">Use a interface [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) em plataformas como IA-64 que exigem registros adicionais.</span><span class="sxs-lookup"><span data-stu-id="4cd08-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cd08-120">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4cd08-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cd08-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4cd08-121">Requirements</span></span>  
 <span data-ttu-id="4cd08-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cd08-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cd08-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cd08-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cd08-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cd08-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cd08-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd08-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd08-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="4cd08-126">See also</span></span>

- [<span data-ttu-id="4cd08-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4cd08-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4cd08-128">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="4cd08-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
