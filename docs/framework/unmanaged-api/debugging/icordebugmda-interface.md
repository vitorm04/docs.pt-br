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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098648"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="32d9a-102">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="32d9a-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="32d9a-103">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="32d9a-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32d9a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="32d9a-104">Methods</span></span>  
  
|<span data-ttu-id="32d9a-105">Método</span><span class="sxs-lookup"><span data-stu-id="32d9a-105">Method</span></span>|<span data-ttu-id="32d9a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="32d9a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32d9a-107">Método GetDescription</span><span class="sxs-lookup"><span data-stu-id="32d9a-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="32d9a-108">Obtém uma cadeia de caracteres que contém uma descrição desse MDA.</span><span class="sxs-lookup"><span data-stu-id="32d9a-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="32d9a-109">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="32d9a-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="32d9a-110">Obtém os sinalizadores associados com esse MDA.</span><span class="sxs-lookup"><span data-stu-id="32d9a-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="32d9a-111">Método GetName</span><span class="sxs-lookup"><span data-stu-id="32d9a-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="32d9a-112">Obtém uma cadeia de caracteres que contém o nome desse MDA.</span><span class="sxs-lookup"><span data-stu-id="32d9a-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="32d9a-113">Método GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="32d9a-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="32d9a-114">Obtém o identificador de thread do sistema operacional no qual esse MDA está em execução.</span><span class="sxs-lookup"><span data-stu-id="32d9a-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="32d9a-115">Método GetXML</span><span class="sxs-lookup"><span data-stu-id="32d9a-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="32d9a-116">Obtém o fluxo XML completo associado a esse MDA.</span><span class="sxs-lookup"><span data-stu-id="32d9a-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32d9a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="32d9a-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32d9a-118">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="32d9a-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d9a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32d9a-119">Requirements</span></span>  
 <span data-ttu-id="32d9a-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32d9a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32d9a-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32d9a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32d9a-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32d9a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32d9a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32d9a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d9a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32d9a-124">See also</span></span>

- [<span data-ttu-id="32d9a-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="32d9a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="32d9a-126">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="32d9a-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
