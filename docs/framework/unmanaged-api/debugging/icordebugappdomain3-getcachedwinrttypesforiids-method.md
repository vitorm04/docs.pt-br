---
title: Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179056"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
Obtém um enumerador para tipos de tempo de execução do Windows em cache em um domínio de aplicativo com base em seus identificadores de interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cReqTypes`  
 [em] O número de tipos necessários.  
  
 `iidsToResolve`  
 [em] Um ponteiro para uma matriz que contém os identificadores de interface correspondentes às representações gerenciadas dos tipos de tempo de execução do Windows a serem recuperados.  
  
 `ppTypesEnum`  
 [fora] Um ponteiro para o endereço de um objeto de interface "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas `iidsToResolve`em cache dos tipos de tempo de execução do Windows recuperados, com base nos identificadores de interface em .  
  
## <a name="remarks"></a>Comentários  
 Se o método não recuperar informações para um identificador de interface específico, a entrada correspondente na `ELEMENT_TYPE_END` coleção "ICorDebugTypeEnum" `ELEMENT_TYPE_VOID` terá um tipo de erros devido a problemas de recuperação de dados ou para identificadores de interface desconhecidos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Tempo de execução do Windows  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)
