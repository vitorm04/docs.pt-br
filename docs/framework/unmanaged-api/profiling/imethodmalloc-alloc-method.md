---
title: Método IMethodMalloc::Alloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447559"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="4a901-102">Método IMethodMalloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="4a901-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="4a901-103">Tenta alocar uma quantidade especificada de memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="4a901-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a901-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a901-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="4a901-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a901-105">Parameters</span></span>

`cb`\
<span data-ttu-id="4a901-106">no O número de bytes a serem alocados para o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="4a901-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a901-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a901-107">Remarks</span></span>

 <span data-ttu-id="4a901-108">A memória alocada começará com um endereço maior que o endereço base do módulo associado a esse alocador.</span><span class="sxs-lookup"><span data-stu-id="4a901-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="4a901-109">Em outras palavras, cada alocador é criado para um módulo específico e tentará alocar memória em um deslocamento positivo de seu endereço base.</span><span class="sxs-lookup"><span data-stu-id="4a901-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="4a901-110">Se `Alloc` falhar em alocar o número solicitado de bytes em um endereço maior do que o endereço base do módulo, ele retornará E_OUTOFMEMORY, independentemente da quantidade real de espaço de memória disponível.</span><span class="sxs-lookup"><span data-stu-id="4a901-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="4a901-111">O método `Alloc` deve ser usado em conjunto com o método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4a901-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a901-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4a901-112">Requirements</span></span>
 <span data-ttu-id="4a901-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a901-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="4a901-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4a901-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="4a901-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a901-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="4a901-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a901-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4a901-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a901-117">See also</span></span>

- [<span data-ttu-id="4a901-118">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="4a901-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
