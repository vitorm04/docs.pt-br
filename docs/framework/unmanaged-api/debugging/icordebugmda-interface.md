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
ms.openlocfilehash: a147aee1ebba57b86dbbf8a7648456b8d7494936
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793192"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="73578-102">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="73578-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="73578-103">Representa uma mensagem do assistente de depuração gerenciado (MDA).</span><span class="sxs-lookup"><span data-stu-id="73578-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73578-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="73578-104">Methods</span></span>  
  
|<span data-ttu-id="73578-105">Método</span><span class="sxs-lookup"><span data-stu-id="73578-105">Method</span></span>|<span data-ttu-id="73578-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="73578-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73578-107">Método GetDescription</span><span class="sxs-lookup"><span data-stu-id="73578-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="73578-108">Obtém uma cadeia de caracteres que contém uma descrição deste MDA.</span><span class="sxs-lookup"><span data-stu-id="73578-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="73578-109">Método GetFlags</span><span class="sxs-lookup"><span data-stu-id="73578-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="73578-110">Obtém os sinalizadores associados a este MDA.</span><span class="sxs-lookup"><span data-stu-id="73578-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="73578-111">Método GetName</span><span class="sxs-lookup"><span data-stu-id="73578-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="73578-112">Obtém uma cadeia de caracteres que contém o nome deste MDA.</span><span class="sxs-lookup"><span data-stu-id="73578-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="73578-113">Método GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="73578-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="73578-114">Obtém o identificador de thread do sistema operacional no qual este MDA está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="73578-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="73578-115">Método GetXML</span><span class="sxs-lookup"><span data-stu-id="73578-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="73578-116">Obtém o fluxo XML completo associado a este MDA.</span><span class="sxs-lookup"><span data-stu-id="73578-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73578-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="73578-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73578-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="73578-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73578-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="73578-119">Requirements</span></span>  
 <span data-ttu-id="73578-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73578-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73578-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73578-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73578-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73578-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73578-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73578-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73578-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="73578-124">See also</span></span>

- [<span data-ttu-id="73578-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="73578-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="73578-126">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="73578-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
