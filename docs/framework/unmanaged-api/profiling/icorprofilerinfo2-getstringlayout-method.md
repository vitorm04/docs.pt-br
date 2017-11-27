---
title: "Método ICorProfilerInfo2::GetStringLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStringLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 52a1b9218feb76f7653f747aa52c44284293221f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>Método ICorProfilerInfo2::GetStringLayout
Obtém informações sobre o layout de um objeto de cadeia de caracteres. Esse método foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]e é substituído pelo [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBufferLengthOffset`  
 [out] Um ponteiro para o deslocamento do local, relativo para o `ObjectID` ponteiro, que armazena o comprimento da cadeia de caracteres. O comprimento é armazenado como um `DWORD`.  
  
> [!NOTE]
>  Este parâmetro retorna o comprimento da cadeia de caracteres em si, não o comprimento do buffer. O comprimento do buffer não está mais disponível.  
  
 `PStringLengthOffset`  
 [out] Um ponteiro para o deslocamento do local, relativo para o `ObjectID` ponteiro, que armazena o comprimento da cadeia de caracteres em si. O comprimento é armazenado como um `DWORD`.  
  
 `pBufferOffset`  
 [out] Um ponteiro para o deslocamento do buffer, relativo para o `ObjectID` ponteiro, que armazena a cadeia de caracteres largos.  
  
## <a name="remarks"></a>Comentários  
 O `GetStringLayout` método obtém os deslocamentos, relativo ao `ObjectID` ponteiro dos locais em que é armazenada a seguir:  
  
-   O comprimento do buffer da cadeia de caracteres.  
  
-   O comprimento da cadeia de caracteres em si.  
  
-   O buffer que contém a cadeia de caracteres largos de real.  
  
 Cadeias de caracteres podem ser terminada em nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
