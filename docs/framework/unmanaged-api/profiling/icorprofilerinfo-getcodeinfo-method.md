---
title: Método ICorProfilerInfo::GetCodeInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 583189cd667af142ab7d0934be34411644dac936
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863914"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>Método ICorProfilerInfo::GetCodeInfo
Obtém a extensão do código nativo associado à ID da função especificada.  
  
 Esse método é obsoleto. Em vez disso, use o método [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função à qual o código nativo está associado.  
  
 `pStart`  
 fora Um ponteiro para uma matriz de bytes que compõe o código nativo da função.  
  
 `pcSize`  
 fora Um ponteiro para um inteiro que especifica o tamanho, em bytes, do código nativo.  
  
## <a name="remarks"></a>Comentários  
 Para otimizar o desempenho, o tempo de execução na versão 2,0 do .NET Framework divide o código pré-compilado precompilado de uma função em várias regiões. Consequentemente, o método `GetCodeInfo` é obsoleto no .NET Framework 2,0 porque não é possível manipular a extensão do código nativo de uma função. Os profileres devem mudar para o uso do método mais geral `ICorProfilerInfo2::GetCodeInfo2` em vez disso.  
  
 Essa função usa buffers alocados pelo chamador.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,0  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
