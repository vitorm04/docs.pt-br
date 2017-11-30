---
title: Interface IMethodMalloc
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a>Interface IMethodMalloc
Fornece um método para alocar memória para um novo corpo de função do Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  O `IMethodMalloc` interface é um alocador de memória simples. Ele permite que você alocar memória, mas não para liberá-la.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ALLOC](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Tenta alocar uma quantidade especificada de memória para um novo corpo de função MSIL.|  
  
## <a name="remarks"></a>Comentários  
 Cada alocador é específico do módulo e garante que o corpo da função estará em um deslocamento positivo de base do módulo. Memória acima de base de um módulo pode ser preciosa, portanto, o alocador de deve ser usado para alocar memória para o corpo da função.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
