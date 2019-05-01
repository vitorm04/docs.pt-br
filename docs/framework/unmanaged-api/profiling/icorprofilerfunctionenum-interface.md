---
title: Interface ICorProfilerFunctionEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e77ec9de198b673bb3b5fc4dad3cd1b0316f07c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991959"
---
# <a name="icorprofilerfunctionenum-interface"></a>Interface ICorProfilerFunctionEnum
Fornece métodos para iterar de forma sequencial por meio de uma coleção de funções no common language runtime.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia deste `ICorProfilerFunctionEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Obtém o número de funções que foram carregados pelo aplicativo ou à força pelo criador de perfil.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Obtém o número especificado de funções contíguos de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Move o cursor do enumerador para a posição inicial da sequência.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos é ignorado.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorProfilerFunctionEnum` interface é um enumerador. Ele permite que o destinatário de uma matriz a elementos de pull do remetente de uma taxa que é apropriado para o receptor. Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas associados com a passagem de matrizes grandes como parâmetros de método.  
  
 `ICorProfilerFunctionEnum` Enumera em funções que já foram compilados pelo JIT, mas não incluem funções que são carregadas de imagens nativas geradas com Ngen.exe.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
