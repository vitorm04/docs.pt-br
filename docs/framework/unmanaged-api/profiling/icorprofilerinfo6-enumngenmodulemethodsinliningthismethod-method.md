---
title: Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 564f3b1cdfab2a3020b6bb5ac8d9af03c6532c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459665"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="f3e02-102">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="f3e02-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="f3e02-103">[Com suporte no .NET Framework 4.6 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="f3e02-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="f3e02-104">Retorna um enumerador para todos os métodos que são definidos em um módulo especificado do NGen e embutido um determinado método.</span><span class="sxs-lookup"><span data-stu-id="f3e02-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e02-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3e02-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3e02-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3e02-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="f3e02-107">[in] O identificador de um módulo do NGen.</span><span class="sxs-lookup"><span data-stu-id="f3e02-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="f3e02-108">[in] O identificador de um módulo que define `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="f3e02-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="f3e02-109">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f3e02-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="f3e02-110">[in] O identificador de um método embutido.</span><span class="sxs-lookup"><span data-stu-id="f3e02-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="f3e02-111">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f3e02-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="f3e02-112">[out] Um sinalizador que indica se `ppEnum` contém todos os métodos de inlining um método específico.</span><span class="sxs-lookup"><span data-stu-id="f3e02-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="f3e02-113">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f3e02-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="f3e02-114">[out] Um ponteiro para o endereço de um enumerador</span><span class="sxs-lookup"><span data-stu-id="f3e02-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e02-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3e02-115">Remarks</span></span>  
 <span data-ttu-id="f3e02-116">`inlineeModuleId` e `inlineeMethodId` juntos, formam o identificador completo para o método que pode ser embutido.</span><span class="sxs-lookup"><span data-stu-id="f3e02-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="f3e02-117">Por exemplo, suponha que o módulo `A` define um método `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="f3e02-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="f3e02-118">módulo Bdefines e `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="f3e02-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="f3e02-119">Suponha também que `Fancy.AddTwice` linhas internas a chamada para `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="f3e02-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="f3e02-120">Um criador de perfil pode usar esse enumerador para localizar todos os métodos definidos no módulo B quais embutido `Simple.Add`, e o resultado seria enumerar `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="f3e02-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="f3e02-121">`inlineeModuleId` é o identificador de módulo `A`, e `inlineeeMethodId` é o identificador de `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="f3e02-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="f3e02-122">Se `incompleteData` ocorre após a função retornar, o enumerador não contém todos os métodos de inlining um determinado método.</span><span class="sxs-lookup"><span data-stu-id="f3e02-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="f3e02-123">Isso pode acontecer quando um ou mais diretas ou indiretas dependências do módulo inliners ainda não foi carregadas ainda.</span><span class="sxs-lookup"><span data-stu-id="f3e02-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="f3e02-124">Se precisar de um criador de perfil dados precisos, ele deve novamente mais tarde quando mais de módulos são carregados, preferencialmente em cada carga de módulo.</span><span class="sxs-lookup"><span data-stu-id="f3e02-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="f3e02-125">O `EnumNgenModuleMethodsInliningThisMethod` método pode ser usado para contornar limitações em inlining para ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f3e02-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="f3e02-126">ReJIT permite um criador de perfil, altere a implementação de um método e, em seguida, criar o novo código para ele em tempo real.</span><span class="sxs-lookup"><span data-stu-id="f3e02-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="f3e02-127">Por exemplo, podemos pode alterar `Simple.Add` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f3e02-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="f3e02-128">No entanto porque `Fancy.AddTwice` tem embutida já `Simple.Add`, ele continuará a ter o mesmo comportamento como antes.</span><span class="sxs-lookup"><span data-stu-id="f3e02-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="f3e02-129">Para contornar essa limitação, o chamador tem que procurar todos os métodos em todos os módulos que embutido `Simple.Add` e usar `ICorProfilerInfo5::RequestRejit` em cada um desses métodos.</span><span class="sxs-lookup"><span data-stu-id="f3e02-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="f3e02-130">Quando os métodos são compilados novamente, eles terão o novo comportamento de `Simple.Add` em vez do comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="f3e02-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e02-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3e02-131">Requirements</span></span>  
 <span data-ttu-id="f3e02-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e02-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e02-133">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3e02-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3e02-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3e02-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e02-135">**Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e02-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e02-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3e02-136">See Also</span></span>  
 [<span data-ttu-id="f3e02-137">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="f3e02-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
