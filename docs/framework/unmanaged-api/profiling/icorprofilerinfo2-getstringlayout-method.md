---
title: Método ICorProfilerInfo2::GetStringLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 71e2bc1d60e050d817429db5bc6926b3b16c637c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431408"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>Método ICorProfilerInfo2::GetStringLayout
Obtém informações sobre o layout de um objeto de cadeia de caracteres. Esse método é preterido no .NET Framework 4 e é substituído pelo método [ICorProfilerInfo3:: GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBufferLengthOffset`  
 fora Um ponteiro para o deslocamento do local, relativo ao ponteiro de `ObjectID`, que armazena o comprimento da cadeia de caracteres. O comprimento é armazenado como um `DWORD`.  
  
> [!NOTE]
> Esse parâmetro retorna o comprimento da cadeia de caracteres em si, não o comprimento do buffer. O comprimento do buffer não está mais disponível.  
  
 `PStringLengthOffset`  
 fora Um ponteiro para o deslocamento do local, relativo ao ponteiro de `ObjectID`, que armazena o comprimento da própria cadeia de caracteres. O comprimento é armazenado como um `DWORD`.  
  
 `pBufferOffset`  
 fora Um ponteiro para o deslocamento do buffer, relativo ao ponteiro de `ObjectID`, que armazena a cadeia de caracteres de largura inteira.  
  
## <a name="remarks"></a>Comentários  
 O método `GetStringLayout` Obtém os deslocamentos, em relação ao ponteiro de `ObjectID`, dos locais nos quais os seguintes itens são armazenados:  
  
- O comprimento do buffer da cadeia de caracteres.  
  
- O comprimento da própria cadeia de caracteres.  
  
- O buffer que contém a cadeia real de caracteres largos.  
  
 Cadeias de caracteres podem ser terminadas em nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
