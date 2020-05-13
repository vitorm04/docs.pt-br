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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213229"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="1919a-102">Interface ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="1919a-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="1919a-103">Representa uma função ou um método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1919a-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1919a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1919a-104">Methods</span></span>  
  
|<span data-ttu-id="1919a-105">Método</span><span class="sxs-lookup"><span data-stu-id="1919a-105">Method</span></span>|<span data-ttu-id="1919a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1919a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1919a-107">Método CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1919a-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="1919a-108">Cria um ponto de interrupção no início desta função.</span><span class="sxs-lookup"><span data-stu-id="1919a-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="1919a-109">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="1919a-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="1919a-110">Obtém um objeto ICorDebugClass que representa a classe da qual essa função é membro.</span><span class="sxs-lookup"><span data-stu-id="1919a-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="1919a-111">Método GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="1919a-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="1919a-112">Obtém o número de versão da edição mais recente feita a esta função.</span><span class="sxs-lookup"><span data-stu-id="1919a-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="1919a-113">Método GetILCode</span><span class="sxs-lookup"><span data-stu-id="1919a-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="1919a-114">Obtém o código da MSIL (Microsoft Intermediate Language) para esta função.</span><span class="sxs-lookup"><span data-stu-id="1919a-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="1919a-115">Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="1919a-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="1919a-116">Obtém o token de metadados para a assinatura de variável local da função que é representada por essa `ICorDebugFunction` instância.</span><span class="sxs-lookup"><span data-stu-id="1919a-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="1919a-117">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="1919a-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="1919a-118">Obtém o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="1919a-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="1919a-119">Método GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="1919a-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="1919a-120">Obtém o código nativo para esta função.</span><span class="sxs-lookup"><span data-stu-id="1919a-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="1919a-121">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="1919a-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="1919a-122">Obtém o token de metadados para esta função.</span><span class="sxs-lookup"><span data-stu-id="1919a-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1919a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1919a-123">Remarks</span></span>  
 <span data-ttu-id="1919a-124">A `ICorDebugFunction` interface não representa uma função com parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1919a-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="1919a-125">Por exemplo, uma `ICorDebugFunction` instância representaria `Func<T>` , mas não `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="1919a-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="1919a-126">Chame [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="1919a-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="1919a-127">A relação entre o token de metadados de um método, o `mdMethodDef` e o objeto de um método `ICorDebugFunction` depende se editar e continuar é permitido na função:</span><span class="sxs-lookup"><span data-stu-id="1919a-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="1919a-128">Se editar e continuar não for permitido na função, existirá uma relação um-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="1919a-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1919a-129">Ou seja, a função tem um `ICorDebugFunction` objeto e um `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="1919a-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="1919a-130">Se editar e continuar for permitido na função, existirá uma relação muitos-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="1919a-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1919a-131">Ou seja, a função pode ter muitas instâncias de `ICorDebugFunction` , uma para cada versão da função, mas apenas um `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="1919a-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1919a-132">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="1919a-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1919a-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1919a-133">Requirements</span></span>  
 <span data-ttu-id="1919a-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1919a-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1919a-135">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1919a-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1919a-136">**Biblioteca:**  CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1919a-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="1919a-137">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1919a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1919a-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="1919a-138">See also</span></span>

- [<span data-ttu-id="1919a-139">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1919a-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
