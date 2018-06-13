---
title: Interface ICorProfilerThreadEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b9662ccb854345d41bb73a5cf01a94b9949891d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457189"
---
# <a name="icorprofilerthreadenum-interface"></a>Interface ICorProfilerThreadEnum
Fornece métodos para iterar em sequência por meio de uma coleção de segmentos no common language runtime.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia deste `ICorProfilerThreadEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|Obtém o número de threads que são usados pelo aplicativo.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|Obtém o número especificado de threads de contíguas de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|Move o cursor do enumerador para a posição inicial da sequência de.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorProfilerThreadEnum` interface é um enumerador. Ele permite que o destinatário de uma matriz para elementos de pull do remetente a uma taxa que é apropriado para o receptor. Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos da matriz, evitando, assim, os problemas associados à transmitindo matrizes grandes como parâmetros de método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
