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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef8d1c47275d3cbd69c1516b788b950f8535513
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737724"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
Obtém um enumerador para os tipos de tempo de execução do Windows em cache em um domínio de aplicativo com base em seus identificadores de interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cReqTypes`  
 [in] O número de tipos necessários.  
  
 `iidsToResolve`  
 [in] Um ponteiro para uma matriz que contém os identificadores de interface correspondente para as representações gerenciadas dos tipos de tempo de execução do Windows a ser recuperado.  
  
 `ppTypesEnum`  
 [out] Um ponteiro para o endereço de um objeto de interface de "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas em cache dos tipos de tempo de execução do Windows recuperados com base em identificadores de interface `iidsToResolve`.  
  
## <a name="remarks"></a>Comentários  
 Se o método falha ao recuperar informações para um identificador de interface específica, a entrada correspondente na coleção "ICorDebugTypeEnum" terão um tipo de `ELEMENT_TYPE_END` erros devido a problemas de recuperação de dados, ou `ELEMENT_TYPE_VOID` para interface desconhecida identificadores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Tempo de Execução do Windows  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugAppDomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
