---
title: ICorDebugFunction2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 190e2323fb07dbca6e156d7a24397997e54b6da9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540787"
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="289ee-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="289ee-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="289ee-103">Estende logicamente a interface ICorDebugFunction para fornecer suporte para depuração apenas meu código passo a passo, que ignora o código de não usuário.</span><span class="sxs-lookup"><span data-stu-id="289ee-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="289ee-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="289ee-104">Methods</span></span>  
  
|<span data-ttu-id="289ee-105">Método</span><span class="sxs-lookup"><span data-stu-id="289ee-105">Method</span></span>|<span data-ttu-id="289ee-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="289ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="289ee-107">Método EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="289ee-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="289ee-108">(Ainda não implementado). Obtém um ponteiro de interface para um que contém as instruções de código nativo na função referenciada por este objeto ICorDebugFunction2 ICorDebugCodeEnum.</span><span class="sxs-lookup"><span data-stu-id="289ee-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="289ee-109">Método GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="289ee-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="289ee-110">Obtém um valor que indica se essa função é marcada como código de usuário.</span><span class="sxs-lookup"><span data-stu-id="289ee-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="289ee-111">Método GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="289ee-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="289ee-112">Obtém a versão de editar e continuar dessa função.</span><span class="sxs-lookup"><span data-stu-id="289ee-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="289ee-113">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="289ee-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="289ee-114">Marca esta função para apenas meu código passo a passo.</span><span class="sxs-lookup"><span data-stu-id="289ee-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="289ee-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="289ee-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="289ee-116">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="289ee-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289ee-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="289ee-117">Requirements</span></span>  
 <span data-ttu-id="289ee-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289ee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289ee-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="289ee-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="289ee-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="289ee-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="289ee-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289ee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289ee-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="289ee-122">See also</span></span>
- [<span data-ttu-id="289ee-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="289ee-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
