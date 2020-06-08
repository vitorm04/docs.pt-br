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
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494196"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="4e133-102">Método IMethodMalloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="4e133-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="4e133-103">Tenta alocar uma quantidade especificada de memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="4e133-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e133-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e133-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="4e133-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e133-105">Parameters</span></span>

`cb`\
<span data-ttu-id="4e133-106">no O número de bytes a serem alocados para o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="4e133-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e133-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e133-107">Remarks</span></span>

 <span data-ttu-id="4e133-108">A memória alocada começará com um endereço maior que o endereço base do módulo associado a esse alocador.</span><span class="sxs-lookup"><span data-stu-id="4e133-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="4e133-109">Em outras palavras, cada alocador é criado para um módulo específico e tentará alocar memória em um deslocamento positivo de seu endereço base.</span><span class="sxs-lookup"><span data-stu-id="4e133-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="4e133-110">Se `Alloc` o falhar em alocar o número solicitado de bytes em um endereço maior que o endereço base do módulo, ele retornará E_OUTOFMEMORY, independentemente da quantidade real de espaço disponível na memória.</span><span class="sxs-lookup"><span data-stu-id="4e133-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="4e133-111">O `Alloc` método deve ser usado em conjunto com o método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4e133-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e133-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e133-112">Requirements</span></span>
 <span data-ttu-id="4e133-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e133-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="4e133-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4e133-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="4e133-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e133-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="4e133-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e133-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4e133-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e133-117">See also</span></span>

- [<span data-ttu-id="4e133-118">Interface IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="4e133-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
