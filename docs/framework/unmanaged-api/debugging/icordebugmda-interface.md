---
title: Interface ICorDebugMDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00a003ee060de59fe0eb8ce8f740a620d77a7c85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="4dd00-102">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="4dd00-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="4dd00-103">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="4dd00-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dd00-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4dd00-104">Methods</span></span>  
  
|<span data-ttu-id="4dd00-105">Método</span><span class="sxs-lookup"><span data-stu-id="4dd00-105">Method</span></span>|<span data-ttu-id="4dd00-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dd00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dd00-107">Método GetDescription</span><span class="sxs-lookup"><span data-stu-id="4dd00-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="4dd00-108">Obtém uma cadeia de caracteres que contém uma descrição do que esse MDA.</span><span class="sxs-lookup"><span data-stu-id="4dd00-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="4dd00-109">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="4dd00-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="4dd00-110">Obtém os sinalizadores associados a esse MDA.</span><span class="sxs-lookup"><span data-stu-id="4dd00-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="4dd00-111">Método GetName</span><span class="sxs-lookup"><span data-stu-id="4dd00-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="4dd00-112">Obtém uma cadeia de caracteres que contém o nome desse MDA.</span><span class="sxs-lookup"><span data-stu-id="4dd00-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="4dd00-113">Método GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="4dd00-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="4dd00-114">Obtém o identificador de thread do sistema operacional em que esse MDA está em execução.</span><span class="sxs-lookup"><span data-stu-id="4dd00-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="4dd00-115">Método GetXML</span><span class="sxs-lookup"><span data-stu-id="4dd00-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="4dd00-116">Obtém o fluxo XML completo associado a esse MDA.</span><span class="sxs-lookup"><span data-stu-id="4dd00-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dd00-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dd00-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dd00-118">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="4dd00-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd00-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dd00-119">Requirements</span></span>  
 <span data-ttu-id="4dd00-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd00-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd00-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dd00-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dd00-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dd00-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dd00-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd00-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd00-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dd00-124">See Also</span></span>  
 [<span data-ttu-id="4dd00-125">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="4dd00-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4dd00-126">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="4dd00-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
