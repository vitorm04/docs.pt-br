---
title: Interface ICorDebugEval2
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4315c9f5296e8c3ffc9d8241b929c71c2448db6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965854"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="9264a-102">Interface ICorDebugEval2</span><span class="sxs-lookup"><span data-stu-id="9264a-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="9264a-103">Estende o "ICorDebugEval" para fornecer suporte para tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="9264a-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9264a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9264a-104">Methods</span></span>  
  
|<span data-ttu-id="9264a-105">Método</span><span class="sxs-lookup"><span data-stu-id="9264a-105">Method</span></span>|<span data-ttu-id="9264a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9264a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9264a-107">Método CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="9264a-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="9264a-108">Define uma chamada para o especificado "ICorDebugFunction", que pode ser aninhada dentro de um tipo cujo construtor usa parâmetros de tipo, ou pode se pegar parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="9264a-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="9264a-109">Método CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="9264a-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="9264a-110">Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de valor nulo ou zero.</span><span class="sxs-lookup"><span data-stu-id="9264a-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="9264a-111">Método NewParameterizedArray</span><span class="sxs-lookup"><span data-stu-id="9264a-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="9264a-112">Aloca uma nova matriz do tipo de elemento especificado e dimensões.</span><span class="sxs-lookup"><span data-stu-id="9264a-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="9264a-113">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="9264a-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="9264a-114">Cria uma instância de um novo objeto de tipo parametrizado e chama o método de construtor do objeto.</span><span class="sxs-lookup"><span data-stu-id="9264a-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="9264a-115">Método NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="9264a-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="9264a-116">Cria uma instância de um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor</span><span class="sxs-lookup"><span data-stu-id="9264a-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="9264a-117">Método NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="9264a-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="9264a-118">Cria uma nova cadeia de caracteres de comprimento especificado com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9264a-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="9264a-119">Método RudeAbort</span><span class="sxs-lookup"><span data-stu-id="9264a-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="9264a-120">Anula o cálculo que este `ICorDebugEval2` está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="9264a-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9264a-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="9264a-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9264a-122">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9264a-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9264a-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9264a-123">Requirements</span></span>  
 <span data-ttu-id="9264a-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9264a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9264a-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9264a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9264a-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9264a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9264a-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9264a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9264a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9264a-128">See also</span></span>
- [<span data-ttu-id="9264a-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9264a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
