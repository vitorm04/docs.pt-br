---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568147"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="aee5a-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span><span class="sxs-lookup"><span data-stu-id="aee5a-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="aee5a-103">[Com suporte no .NET Framework 4.6 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="aee5a-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="aee5a-104">Retorna um enumerador para todos os métodos que são definidos em um determinado módulo do NGen e embutida de um determinado método.</span><span class="sxs-lookup"><span data-stu-id="aee5a-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee5a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aee5a-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aee5a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aee5a-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="aee5a-107">[in] O identificador de um módulo do NGen.</span><span class="sxs-lookup"><span data-stu-id="aee5a-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="aee5a-108">[in] O identificador de um módulo que define `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="aee5a-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="aee5a-109">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aee5a-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="aee5a-110">[in] O identificador de um método embutido.</span><span class="sxs-lookup"><span data-stu-id="aee5a-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="aee5a-111">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aee5a-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="aee5a-112">[out] Um sinalizador que indica se `ppEnum` contém todos os métodos de embutidos um determinado método.</span><span class="sxs-lookup"><span data-stu-id="aee5a-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="aee5a-113">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aee5a-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="aee5a-114">[out] Um ponteiro para o endereço de um enumerador</span><span class="sxs-lookup"><span data-stu-id="aee5a-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aee5a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="aee5a-115">Remarks</span></span>  
 <span data-ttu-id="aee5a-116">`inlineeModuleId` e `inlineeMethodId` juntos, formam o identificador completo para o método que pode ser embutido.</span><span class="sxs-lookup"><span data-stu-id="aee5a-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="aee5a-117">Por exemplo, suponha que o módulo `A` define um método `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="aee5a-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="aee5a-118">e o módulo Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="aee5a-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="aee5a-119">Vamos supor também que `Fancy.AddTwice` inlines a chamada para `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="aee5a-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="aee5a-120">Um criador de perfil pode usar este enumerador para localizar todos os métodos definidos no módulo B qual embutido `Simple.Add`, e o resultado seria enumerar `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="aee5a-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="aee5a-121">`inlineeModuleId` é o identificador do módulo `A`, e `inlineeeMethodId` é o identificador do `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="aee5a-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="aee5a-122">Se `incompleteData` é verdadeiro após a função retornar, o enumerador não contém todos os métodos de embutidos um determinado método.</span><span class="sxs-lookup"><span data-stu-id="aee5a-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="aee5a-123">Isso pode acontecer quando um ou mais dependências diretas ou indiretas do módulo inliners ainda não foi carregadas ainda.</span><span class="sxs-lookup"><span data-stu-id="aee5a-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="aee5a-124">Se um criador de perfil precisa dados precisos, ele deve novamente mais tarde quando mais módulos são carregados, preferencialmente na carga de cada módulo.</span><span class="sxs-lookup"><span data-stu-id="aee5a-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="aee5a-125">O `EnumNgenModuleMethodsInliningThisMethod` método pode ser usado para contornar limitações em inlining para ReJIT.</span><span class="sxs-lookup"><span data-stu-id="aee5a-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="aee5a-126">Permite que um criador de perfil do ReJIT alterar a implementação de um método e, em seguida, crie o novo código para ele em tempo real.</span><span class="sxs-lookup"><span data-stu-id="aee5a-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="aee5a-127">Por exemplo, podemos pode alterar `Simple.Add` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aee5a-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="aee5a-128">No entanto porque `Fancy.AddTwice` tem já embutida `Simple.Add`, ele continua a ter o mesmo comportamento como antes.</span><span class="sxs-lookup"><span data-stu-id="aee5a-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="aee5a-129">Para contornar essa limitação, o chamador tenha que pesquisar todos os métodos em todos os módulos isso de forma embutida `Simple.Add` e use `ICorProfilerInfo5::RequestRejit` em cada um desses métodos.</span><span class="sxs-lookup"><span data-stu-id="aee5a-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="aee5a-130">Quando os métodos são compilados novamente, eles terão o novo comportamento da `Simple.Add` em vez do comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="aee5a-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee5a-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aee5a-131">Requirements</span></span>  
 <span data-ttu-id="aee5a-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aee5a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee5a-133">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aee5a-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aee5a-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aee5a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aee5a-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee5a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee5a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aee5a-136">See also</span></span>
- [<span data-ttu-id="aee5a-137">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="aee5a-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
