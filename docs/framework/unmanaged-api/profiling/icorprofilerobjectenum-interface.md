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
ms.openlocfilehash: fce89cc2b3b0104ba017b7df9105dea3f6ec4e91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868220"
---
# <a name="icorprofilerobjectenum-interface"></a>Interface ICorProfilerObjectEnum
Fornece métodos para iterar em sequência por meio de uma coleção de objetos congelados que são gerados pelo [NGen. exe (gerador de imagem nativa)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](icorprofilerobjectenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia desta `ICorProfilerObjectEnum` interface.|  
|[Método GetCount](icorprofilerobjectenum-getcount-method.md)|Obtém o número total de objetos congelados na coleção.|  
|[Método Next](icorprofilerobjectenum-next-method.md)|Obtém o número especificado de objetos contíguos de uma coleção sequencial de objetos, começando na posição atual do enumerador na sequência.|  
|[Método Reset](icorprofilerobjectenum-reset-method.md)|Move o cursor deste enumerador para a posição inicial da sequência.|  
|[Método Skip](icorprofilerobjectenum-skip-method.md)|Avança o cursor deste enumerador de sua posição atual para que o número especificado de elementos seja ignorado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorProfilerObjectEnum` é um enumerador. Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário. Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas relacionados à passagem de matrizes grandes como parâmetros de método.  
  
 Use [ICorProfilerInfo2:: EnumModuleFrozenObjects](icorprofilerinfo2-enummodulefrozenobjects-method.md) para obter um ponteiro para a interface `ICorProfilerObjectEnum`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Método EnumModuleFrozenObjects](icorprofilerinfo2-enummodulefrozenobjects-method.md)
