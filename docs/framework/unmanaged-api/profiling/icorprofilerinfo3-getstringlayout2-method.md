---
title: Método ICorProfilerInfo3::GetStringLayout2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862250"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>Método ICorProfilerInfo3::GetStringLayout2
Obtém informações sobre o layout de um objeto de cadeia de caracteres. Esse método substitui o método [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pStringLengthOffset`  
 fora Um ponteiro para o deslocamento do local, relativo ao ponteiro de `ObjectID`, que armazena o comprimento da própria cadeia de caracteres. O comprimento é armazenado como um `DWORD`.  
  
 `pBufferOffset`  
 fora Um ponteiro para o deslocamento do buffer, relativo ao ponteiro de `ObjectID`, que armazena a cadeia de caracteres de largura inteira.  
  
## <a name="remarks"></a>Comentários  
 Cadeias de caracteres podem ou não ser terminadas em nulo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
