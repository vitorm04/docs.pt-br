---
title: Interface ICorDebugFunction2
ms.date: 03/30/2017
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
ms.openlocfilehash: da440b7d2da57511545d3b63700662eb544660fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137771"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="45898-102">Interface ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="45898-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="45898-103">Estende logicamente a interface ICorDebugFunction para fornecer suporte para depuração passo a Apenas Meu Código, que ignora o código que não é do usuário.</span><span class="sxs-lookup"><span data-stu-id="45898-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45898-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="45898-104">Methods</span></span>  
  
|<span data-ttu-id="45898-105">Método</span><span class="sxs-lookup"><span data-stu-id="45898-105">Method</span></span>|<span data-ttu-id="45898-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="45898-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45898-107">Método EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="45898-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="45898-108">(Ainda não implementado.) Obtém um ponteiro de interface para um ICorDebugCodeEnum que contém as instruções de código nativo na função referenciada por este objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="45898-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="45898-109">Método GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="45898-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="45898-110">Obtém um valor que indica se esta função está marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="45898-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="45898-111">Método GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="45898-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="45898-112">Obtém a versão editar e continuar desta função.</span><span class="sxs-lookup"><span data-stu-id="45898-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="45898-113">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="45898-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="45898-114">Marca essa função para Apenas Meu Código stepping.</span><span class="sxs-lookup"><span data-stu-id="45898-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45898-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="45898-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45898-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="45898-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45898-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45898-117">Requirements</span></span>  
 <span data-ttu-id="45898-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45898-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45898-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45898-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45898-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45898-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45898-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45898-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45898-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45898-122">See also</span></span>

- [<span data-ttu-id="45898-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="45898-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
