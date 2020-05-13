---
title: Interface ICorDebugMDA
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: d711f36b4e2071dac9458a023e1d3cf4743e77b3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212627"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="acf34-102">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="acf34-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="acf34-103">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="acf34-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acf34-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="acf34-104">Methods</span></span>  
  
|<span data-ttu-id="acf34-105">Método</span><span class="sxs-lookup"><span data-stu-id="acf34-105">Method</span></span>|<span data-ttu-id="acf34-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="acf34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acf34-107">Método GetDescription</span><span class="sxs-lookup"><span data-stu-id="acf34-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="acf34-108">Obtém uma cadeia de caracteres que contém uma descrição deste MDA.</span><span class="sxs-lookup"><span data-stu-id="acf34-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="acf34-109">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="acf34-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="acf34-110">Obtém os sinalizadores associados a este MDA.</span><span class="sxs-lookup"><span data-stu-id="acf34-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="acf34-111">Método GetName</span><span class="sxs-lookup"><span data-stu-id="acf34-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="acf34-112">Obtém uma cadeia de caracteres que contém o nome deste MDA.</span><span class="sxs-lookup"><span data-stu-id="acf34-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="acf34-113">Método GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="acf34-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="acf34-114">Obtém o identificador de thread do sistema operacional no qual este MDA está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="acf34-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="acf34-115">Método GetXML</span><span class="sxs-lookup"><span data-stu-id="acf34-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="acf34-116">Obtém o fluxo XML completo associado a este MDA.</span><span class="sxs-lookup"><span data-stu-id="acf34-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf34-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="acf34-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acf34-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="acf34-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf34-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="acf34-119">Requirements</span></span>  
 <span data-ttu-id="acf34-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acf34-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acf34-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acf34-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acf34-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acf34-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acf34-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acf34-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf34-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="acf34-124">See also</span></span>

- [<span data-ttu-id="acf34-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="acf34-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="acf34-126">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="acf34-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
