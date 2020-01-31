---
title: Método ICorProfilerCallback::AssemblyLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866635"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>Método ICorProfilerCallback::AssemblyLoadFinished
Notifica o criador de perfil que concluiu o carregamento de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parâmetros

- `assemblyId`

  \[em] identifica o assembly que foi carregado.

- `hrStatus`

  \[em] um HRESULT que indica se o assembly terminou de ser carregado com êxito.

## <a name="remarks"></a>Comentários  
 O valor de `assemblyId` não é válido para uma solicitação de informações até que o método `AssemblyLoadFinished` seja chamado.  
  
 Algumas partes do carregamento do assembly podem continuar depois do `AssemblyLoadFinished` retorno de chamada. Uma falha HRESULT no `hrStatus` indica uma falha. No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento do assembly foi bem-sucedida.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
