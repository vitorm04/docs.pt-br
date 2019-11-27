---
title: Método ICorProfilerInfo2::GetClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433397"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>Método ICorProfilerInfo2::GetClassLayout
Obtém informações sobre o layout, na memória, dos campos definidos pela classe especificada. Ou seja, esse método obtém os deslocamentos dos campos da classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classID`  
 no A ID da classe para a qual o layout será recuperado.  
  
 `rFieldOffset`  
 [entrada, saída] Uma matriz de estruturas [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , cada uma delas contém os tokens e os deslocamentos dos campos da classe.  
  
 `cFieldOffset`  
 no O tamanho da matriz de `rFieldOffset`.  
  
 `pcFieldOffset`  
 fora Um ponteiro para o número total de elementos disponíveis. Se `cFieldOffset` for 0, esse valor indicará o número de elementos necessários.  
  
 `pulClassSize`  
 fora Um ponteiro para um local que contém o tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 O método `GetClassLayout` retorna apenas os campos definidos pela própria classe. Se a classe pai da classe também tiver campos definidos, o criador de perfil deverá chamar `GetClassLayout` na classe pai para obter esses campos.  
  
 Se você usar `GetClassLayout` com classes de cadeia de caracteres, o método falhará com o código de erro E_INVALIDARG. Use [ICorProfilerInfo2:: GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) para obter informações sobre o layout de uma cadeia de caracteres. `GetClassLayout` também falhará quando chamado com uma classe de matriz.  
  
 Depois que `GetClassLayout` retorna, você deve verificar se o buffer de `rFieldOffset` era grande o suficiente para conter todas as estruturas de `COR_FIELD_OFFSET` disponíveis. Para fazer isso, compare o valor que `pcFieldOffset` aponta com o tamanho de `rFieldOffset` dividido pelo tamanho de uma estrutura de `COR_FIELD_OFFSET`. Se `rFieldOffset` não for grande o suficiente, aloque um buffer de `rFieldOffset` maior, atualize `cFieldOffset` com o tamanho novo, maior e chame `GetClassLayout` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetClassLayout` com um buffer de `rFieldOffset` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcFieldOffset` e chamar `GetClassLayout` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
