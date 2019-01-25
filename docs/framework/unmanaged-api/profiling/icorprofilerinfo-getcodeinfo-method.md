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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5004de587f715a2f3958c36999e432d7d6e9f2fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632654"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>Método ICorProfilerInfo::GetCodeInfo
Obtém a extensão do código nativo associado com a ID da função especificada.  
  
 Esse método é obsoleto. Use o [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função à qual o código nativo está associado.  
  
 `pStart`  
 [out] Um ponteiro para uma matriz de bytes que compõem o código nativo da função.  
  
 `pcSize`  
 [out] Um ponteiro para um inteiro que especifica o tamanho, em bytes, do código nativo.  
  
## <a name="remarks"></a>Comentários  
 Para otimizar o desempenho, o tempo de execução no .NET Framework versão 2.0 divide o código nativo pré-compilado de uma função em várias regiões. Consequentemente, o `GetCodeInfo` método está obsoleto no .NET Framework 2.0, porque não é possível lidar com a extensão do código nativo da função. Os criadores de perfis devem passar a usar o mais geral `ICorProfilerInfo2::GetCodeInfo2` método em vez disso.  
  
 Essa função usa buffers alocados pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.0  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
