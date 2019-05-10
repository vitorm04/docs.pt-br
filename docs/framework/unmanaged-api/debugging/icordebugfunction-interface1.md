---
title: Interface ICorDebugFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550b85474c1ccd7e125549e86df906439caf410e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621493"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="75077-102">Interface ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="75077-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="75077-103">Representa uma função ou um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="75077-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75077-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="75077-104">Methods</span></span>  
  
|<span data-ttu-id="75077-105">Método</span><span class="sxs-lookup"><span data-stu-id="75077-105">Method</span></span>|<span data-ttu-id="75077-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="75077-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75077-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="75077-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="75077-108">Cria um ponto de interrupção no início desta função.</span><span class="sxs-lookup"><span data-stu-id="75077-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="75077-109">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="75077-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="75077-110">Obtém um objeto ICorDebugClass que representa essa função é um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="75077-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="75077-111">Método GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="75077-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="75077-112">Obtém o número de versão da edição mais recente feita para essa função.</span><span class="sxs-lookup"><span data-stu-id="75077-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="75077-113">Método GetILCode</span><span class="sxs-lookup"><span data-stu-id="75077-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="75077-114">Obtém o código do Microsoft intermediate language (MSIL) para essa função.</span><span class="sxs-lookup"><span data-stu-id="75077-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="75077-115">Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="75077-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="75077-116">Obtém os metadados de token para a assinatura de variável local da função que é representada por esse `ICorDebugFunction` instância.</span><span class="sxs-lookup"><span data-stu-id="75077-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="75077-117">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="75077-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="75077-118">Obtém o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="75077-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="75077-119">Método GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="75077-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="75077-120">Obtém o código nativo para essa função.</span><span class="sxs-lookup"><span data-stu-id="75077-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="75077-121">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="75077-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="75077-122">Obtém os metadados de token para essa função.</span><span class="sxs-lookup"><span data-stu-id="75077-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75077-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="75077-123">Remarks</span></span>  
 <span data-ttu-id="75077-124">O `ICorDebugFunction` interface não representa uma função com parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="75077-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="75077-125">Por exemplo, um `ICorDebugFunction` instância representariam `Func<T>` , mas não `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="75077-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="75077-126">Chame [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="75077-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="75077-127">A relação entre o token de metadados de um método `mdMethodDef`e um método `ICorDebugFunction` objeto é dependente de editar e continuar é permitida na função:</span><span class="sxs-lookup"><span data-stu-id="75077-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="75077-128">Se editar e continuar não é permitida na função, existe uma relação um para um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="75077-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="75077-129">Ou seja, a função tem um `ICorDebugFunction` objeto e um `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="75077-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="75077-130">Se editar e continuar é permitida na função, existe uma relação de muitos-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="75077-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="75077-131">Ou seja, a função pode ter muitas instâncias do `ICorDebugFunction`, um para cada versão da função, mas somente um `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="75077-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75077-132">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="75077-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75077-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75077-133">Requirements</span></span>  
 <span data-ttu-id="75077-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75077-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75077-135">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75077-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75077-136">**Biblioteca:**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75077-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="75077-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75077-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75077-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75077-138">See also</span></span>

- [<span data-ttu-id="75077-139">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="75077-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
