---
title: Interface1 ICorDebugFunction2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="62ece-102">Interface1 ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="62ece-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="62ece-103">Logicamente estende a interface ICorDebugFunction para fornecer suporte para apenas meu código passo a passo de depuração, que ignora o código não-usuário.</span><span class="sxs-lookup"><span data-stu-id="62ece-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62ece-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="62ece-104">Methods</span></span>  
  
|<span data-ttu-id="62ece-105">Método</span><span class="sxs-lookup"><span data-stu-id="62ece-105">Method</span></span>|<span data-ttu-id="62ece-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="62ece-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62ece-107">Método EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="62ece-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="62ece-108">(Ainda não implementado). Obtém um ponteiro de interface para um que contém as instruções de código nativo na função referenciada por este objeto ICorDebugFunction2 ICorDebugCodeEnum.</span><span class="sxs-lookup"><span data-stu-id="62ece-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="62ece-109">Método GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="62ece-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="62ece-110">Obtém um valor que indica se essa função é marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="62ece-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="62ece-111">Método GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="62ece-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="62ece-112">Obtém a versão de editar e continuar dessa função.</span><span class="sxs-lookup"><span data-stu-id="62ece-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="62ece-113">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="62ece-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="62ece-114">Marca esta função para apenas meu código passo a passo.</span><span class="sxs-lookup"><span data-stu-id="62ece-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62ece-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="62ece-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62ece-116">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="62ece-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ece-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62ece-117">Requirements</span></span>  
 <span data-ttu-id="62ece-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ece-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ece-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62ece-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62ece-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ece-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ece-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ece-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ece-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62ece-122">See Also</span></span>  
 [<span data-ttu-id="62ece-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="62ece-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
