---
title: Método ICorProfilerInfo::GetILFunctionBodyAllocator
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 5fe472c4a0053ec9e37d7d61ffde5cf21d65dd2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863459"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>Método ICorProfilerInfo::GetILFunctionBodyAllocator
Obtém uma interface que fornece um método para alocar memória a ser usada para alternar o corpo de um método no código MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo no qual o método reside.  
  
 `ppMalloc`  
 fora Um ponteiro para uma interface [IMethodMalloc](imethodmalloc-interface.md) que fornece um método para alocar a memória.  
  
## <a name="remarks"></a>Comentários  
 Um corpo de método no código MSIL deve estar localizado como um endereço virtual relativo (RVA), relativo ao módulo carregado, o que significa que ele segue o módulo dentro de 4 GB. Para tornar mais fácil para uma ferramenta alternar o corpo de um método, o método `GetILFunctionBodyAllocator` garante que a memória seja alocada dentro desse intervalo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
