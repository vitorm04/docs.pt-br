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
# <a name="imethodmallocalloc-method"></a>Método IMethodMalloc::Alloc

Tenta alocar uma quantidade especificada de memória para um novo corpo de função da MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Sintaxe

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parâmetros

`cb`\
no O número de bytes a serem alocados para o corpo do método.

## <a name="remarks"></a>Comentários

 A memória alocada começará com um endereço maior que o endereço base do módulo associado a esse alocador. Em outras palavras, cada alocador é criado para um módulo específico e tentará alocar memória em um deslocamento positivo de seu endereço base. Se `Alloc` falhar em alocar o número solicitado de bytes em um endereço maior do que o endereço base do módulo, ele retornará E_OUTOFMEMORY, independentemente da quantidade real de espaço de memória disponível.

 O método `Alloc` deve ser usado em conjunto com o método [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** CorProf. idl, CorProf. h

 **Biblioteca:** CorGuids.lib

 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface IMethodMalloc](imethodmalloc-interface.md)
