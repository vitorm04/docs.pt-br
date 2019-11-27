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
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447800"
---
# <a name="icorprofilerfunctionenum-interface"></a>Interface ICorProfilerFunctionEnum
Fornece métodos para iterar em sequência por meio de uma coleção de funções no Common Language Runtime.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia desta `ICorProfilerFunctionEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Obtém o número de funções que foram carregadas pelo aplicativo ou carregadas de modo forçado pelo criador de perfil.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Obtém o número especificado de funções contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Move o cursor do enumerador para a posição inicial da sequência.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos seja ignorado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorProfilerFunctionEnum` é um enumerador. Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário. Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando, assim, os problemas associados à passagem de matrizes grandes como parâmetros de método.  
  
 `ICorProfilerFunctionEnum` enumera em funções que já foram compiladas por JIT, mas não inclui funções que são carregadas de imagens nativas geradas com NGen. exe.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
