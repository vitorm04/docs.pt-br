---
title: Método ICorProfilerInfo::GetObjectSize
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: b860cf6eb07c3f063e3e51514f8492cf4af9e8ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869666"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>Método ICorProfilerInfo::GetObjectSize
Obtém o tamanho de um objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 no A ID do objeto.  
  
 `pcSize`  
 fora Um ponteiro para o tamanho do objeto, em bytes.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Esse método é obsoleto. Ele retorna COR_E_OVERFLOW para objetos com mais de 4 GB em plataformas de 64 bits. Em vez disso, use o método [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) .  
  
 Objetos diferentes dos mesmos tipos geralmente têm o mesmo tamanho. No entanto, alguns tipos, como matrizes ou cadeias de caracteres, podem ter um tamanho diferente para cada objeto.  
  
 O tamanho retornado pelo método `GetObjectSize` não inclui nenhum preenchimento de alinhamento que possa aparecer depois que o objeto estiver no heap de coleta de lixo. Se você usar o método `GetObjectSize` para avançar do objeto para o objeto no heap de coleta de lixo, adicione manualmente o preenchimento de alinhamento, conforme necessário.  
  
- No Windows de 32 bits, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 e COR_PRF_GC_GEN_2 usam o alinhamento de 4 bytes e COR_PRF_GC_LARGE_OBJECT_HEAP usa o alinhamento de 8 bytes.  
  
- No Windows de 64 bits, o alinhamento é sempre de 8 bytes.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
