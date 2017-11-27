---
title: Interface1 ICorDebugEval2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="043e3-102">Interface1 ICorDebugEval2</span><span class="sxs-lookup"><span data-stu-id="043e3-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="043e3-103">Estende "ICorDebugEval" para oferecer suporte para tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="043e3-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="043e3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="043e3-104">Methods</span></span>  
  
|<span data-ttu-id="043e3-105">Método</span><span class="sxs-lookup"><span data-stu-id="043e3-105">Method</span></span>|<span data-ttu-id="043e3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="043e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="043e3-107">Método CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="043e3-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="043e3-108">Configura uma chamada para o especificado "ICorDebugFunction", que pode ser aninhada dentro de um tipo cujo construtor usa parâmetros de tipo ou em si pode usar parâmetros de tipos.</span><span class="sxs-lookup"><span data-stu-id="043e3-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="043e3-109">Método CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="043e3-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="043e3-110">Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de nulo ou zero.</span><span class="sxs-lookup"><span data-stu-id="043e3-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="043e3-111">Método NewParameterizedArray</span><span class="sxs-lookup"><span data-stu-id="043e3-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="043e3-112">Aloca uma nova matriz do tipo de elemento especificado e dimensões.</span><span class="sxs-lookup"><span data-stu-id="043e3-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="043e3-113">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="043e3-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="043e3-114">Cria um novo objeto de tipo parametrizado e chama o método de construtor do objeto.</span><span class="sxs-lookup"><span data-stu-id="043e3-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="043e3-115">Método NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="043e3-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="043e3-116">Cria um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor</span><span class="sxs-lookup"><span data-stu-id="043e3-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="043e3-117">Método NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="043e3-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="043e3-118">Cria uma nova cadeia de caracteres de comprimento especificado com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="043e3-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="043e3-119">Método RudeAbort</span><span class="sxs-lookup"><span data-stu-id="043e3-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="043e3-120">Anula o cálculo que este `ICorDebugEval2` está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="043e3-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="043e3-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="043e3-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="043e3-122">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="043e3-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="043e3-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="043e3-123">Requirements</span></span>  
 <span data-ttu-id="043e3-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="043e3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="043e3-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="043e3-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="043e3-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="043e3-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="043e3-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="043e3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043e3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="043e3-128">See Also</span></span>  
 [<span data-ttu-id="043e3-129">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="043e3-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
