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
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784900"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
Obtém um enumerador para tipos de Windows Runtime em cache em um domínio de aplicativo com base em seus identificadores de interface.  
  
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
 no O número de tipos necessários.  
  
 `iidsToResolve`  
 no Um ponteiro para uma matriz que contém os identificadores de interface correspondentes às representações gerenciadas dos tipos de Windows Runtime a serem recuperados.  
  
 `ppTypesEnum`  
 fora Um ponteiro para o endereço de um objeto de interface "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas em cache dos tipos de Windows Runtime recuperados, com base nos identificadores de interface no `iidsToResolve`.  
  
## <a name="remarks"></a>Comentários  
 Se o método não conseguir recuperar informações para um identificador de interface específico, a entrada correspondente na coleção "ICorDebugTypeEnum" terá um tipo de `ELEMENT_TYPE_END` para erros devido a problemas de recuperação de dados ou `ELEMENT_TYPE_VOID` para identificadores de interface desconhecidos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** Windows Runtime  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)
