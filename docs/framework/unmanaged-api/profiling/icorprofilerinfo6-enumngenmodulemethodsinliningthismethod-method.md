---
title: Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495522"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="37be2-102">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="37be2-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="37be2-103">Retorna um enumerador para todos os métodos que são definidos em um determinado módulo NGen e embutidos em um determinado método.</span><span class="sxs-lookup"><span data-stu-id="37be2-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="37be2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37be2-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="37be2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37be2-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="37be2-106">no O identificador de um módulo NGen.</span><span class="sxs-lookup"><span data-stu-id="37be2-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="37be2-107">no O identificador de um módulo que define `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="37be2-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="37be2-108">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="37be2-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="37be2-109">no O identificador de um método embutido.</span><span class="sxs-lookup"><span data-stu-id="37be2-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="37be2-110">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="37be2-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="37be2-111">fora Um sinalizador que indica se `ppEnum` o contém todos os métodos que indefinem um determinado método.</span><span class="sxs-lookup"><span data-stu-id="37be2-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="37be2-112">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="37be2-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="37be2-113">fora Um ponteiro para o endereço de um enumerador</span><span class="sxs-lookup"><span data-stu-id="37be2-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="37be2-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="37be2-114">Remarks</span></span>

<span data-ttu-id="37be2-115">`inlineeModuleId`e, `inlineeMethodId` juntos, formam o identificador completo do método que pode ser embutido.</span><span class="sxs-lookup"><span data-stu-id="37be2-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="37be2-116">Por exemplo, suponha que `A` o módulo defina um método `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="37be2-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="37be2-117">e o módulo B define `Fancy.AddTwice` :</span><span class="sxs-lookup"><span data-stu-id="37be2-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="37be2-118">Vamos supor também que `Fancy.AddTwice` o embutirá a chamada para `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="37be2-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="37be2-119">Um criador de perfil pode usar esse enumerador para localizar todos os métodos definidos no módulo B que está embutido `Simple.Add` e o resultado seria enumerado `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="37be2-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="37be2-120">`inlineeModuleId`é o identificador do módulo `A` e `inlineeMethodId` é o identificador de `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="37be2-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="37be2-121">Se `incompleteData` for true Depois que a função retornar, o enumerador não conterá todos os métodos inalinhando um determinado método.</span><span class="sxs-lookup"><span data-stu-id="37be2-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="37be2-122">Isso pode acontecer quando uma ou mais dependências diretas ou indiretas do módulo inlineers ainda não foram carregadas.</span><span class="sxs-lookup"><span data-stu-id="37be2-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="37be2-123">Se um criador de perfil precisar de dados precisos, ele deverá tentar novamente mais tarde quando mais módulos forem carregados, preferencialmente em cada carregamento de módulo.</span><span class="sxs-lookup"><span data-stu-id="37be2-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="37be2-124">O `EnumNgenModuleMethodsInliningThisMethod` método pode ser usado para solucionar limitações de inalinhamento para ReJIT.</span><span class="sxs-lookup"><span data-stu-id="37be2-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="37be2-125">O ReJIT permite que um criador de perfil altere a implementação de um método e, em seguida, crie um novo código para ele em tempo real.</span><span class="sxs-lookup"><span data-stu-id="37be2-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="37be2-126">Por exemplo, poderíamos mudar da `Simple.Add` seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="37be2-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="37be2-127">No entanto `Fancy.AddTwice` , como já foi embutido `Simple.Add` , ele continua tendo o mesmo comportamento que antes.</span><span class="sxs-lookup"><span data-stu-id="37be2-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="37be2-128">Para contornar essa limitação, o chamador precisa pesquisar todos os métodos em todos os módulos que embutidos `Simple.Add` e usar `ICorProfilerInfo5::RequestRejit` em cada um desses métodos.</span><span class="sxs-lookup"><span data-stu-id="37be2-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="37be2-129">Quando os métodos forem compilados novamente, eles terão o novo comportamento do `Simple.Add` em vez do comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="37be2-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="37be2-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37be2-130">Requirements</span></span>

<span data-ttu-id="37be2-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37be2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="37be2-132">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="37be2-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="37be2-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37be2-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="37be2-134">**.NET Framework versões:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37be2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="37be2-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="37be2-135">See also</span></span>

- [<span data-ttu-id="37be2-136">Interface ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="37be2-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
