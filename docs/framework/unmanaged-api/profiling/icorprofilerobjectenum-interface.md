---
title: Interface ICorProfilerObjectEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
ms.openlocfilehash: 95dce47a65bd437525011d2c1588d7e13adac85b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428175"
---
# <a name="icorprofilerobjectenum-interface"></a>Interface ICorProfilerObjectEnum
Fornece métodos para iterar em sequência por meio de uma coleção de objetos congelados que são gerados pelo [NGen. exe (gerador de imagem nativa)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia desta `ICorProfilerObjectEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Obtém o número total de objetos congelados na coleção.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Obtém o número especificado de objetos contíguos de uma coleção sequencial de objetos, começando na posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Move o cursor deste enumerador para a posição inicial da sequência.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Avança o cursor deste enumerador de sua posição atual para que o número especificado de elementos seja ignorado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorProfilerObjectEnum` é um enumerador. Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário. Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas relacionados à passagem de matrizes grandes como parâmetros de método.  
  
 Use [ICorProfilerInfo2:: EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) para obter um ponteiro para a interface `ICorProfilerObjectEnum`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
