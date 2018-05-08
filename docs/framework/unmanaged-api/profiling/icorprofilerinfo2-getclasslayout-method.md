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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>Método ICorProfilerInfo2::GetClassLayout
Obtém informações sobre o layout, na memória, os campos definidos pela classe especificada. Ou seja, esse método obtém os deslocamentos de campos da classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classID`  
 [in] A ID da classe para a qual o layout será recuperado.  
  
 `rFieldOffset`  
 [out no] Uma matriz de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) estruturas, cada qual contendo os tokens e deslocamentos de campos da classe.  
  
 `cFieldOffset`  
 [in] O tamanho do `rFieldOffset` matriz.  
  
 `pcFieldOffset`  
 [out] Um ponteiro para o número total de elementos disponíveis. Se `cFieldOffset` for 0, esse valor indica o número de elementos necessários.  
  
 `pulClassSize`  
 [out] Um ponteiro para um local que contém o tamanho, em bytes, da classe.  
  
## <a name="remarks"></a>Comentários  
 O `GetClassLayout` método retorna apenas os campos definidos pela classe em si. Se a classe do pai definiu campos, o criador de perfil deve chamar `GetClassLayout` na classe pai para obter esses campos.  
  
 Se você usar `GetClassLayout` com classes de cadeia de caracteres, o método falhará com o código de erro E_INVALIDARG. Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) para obter informações sobre o layout de uma cadeia de caracteres. `GetClassLayout` também falharão quando chamado com uma classe de matriz.  
  
 Depois de `GetClassLayout` retorna, você deve verificar se o `rFieldOffset` buffer era grande o suficiente para conter todos os disponíveis `COR_FIELD_OFFSET` estruturas. Para fazer isso, o valor de comparação que `pcFieldOffset` aponta para o tamanho de `rFieldOffset` dividida pelo tamanho de um `COR_FIELD_OFFSET` estrutura. Se `rFieldOffset` não é grande o suficiente, alocar uma maior `rFieldOffset` buffer, atualize `cFieldOffset` com o novo tamanho maior e chame `GetClassLayout` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetClassLayout` com um comprimento zero `rFieldOffset` buffer para obter o tamanho do buffer correto. Você pode definir o tamanho do buffer para o valor retornado em `pcFieldOffset` e chame `GetClassLayout` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
