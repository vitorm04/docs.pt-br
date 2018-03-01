---
title: "Método IMethodMalloc::Alloc"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a>Método IMethodMalloc::Alloc
Tenta alocar uma quantidade especificada de memória para um novo corpo de função do Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cb`  
 [in] O número de bytes a ser alocada para o corpo do método.  
  
## <a name="remarks"></a>Comentários  
 A memória alocada será iniciado em um maior que o endereço base do módulo que está associado este alocador de endereço. Em outras palavras, cada alocador é criado para um módulo específico e tentará alocar memória em um deslocamento positivo de seu endereço base. Se `Alloc` Falha ao alocar o número solicitado de bytes em um endereço maior que o endereço base do módulo, ele retorna E_OUTOFMEMORY, independentemente da quantidade real de espaço de memória disponível.  
  
 O `Alloc` método deve ser usado em conjunto com o [: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** WindSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
