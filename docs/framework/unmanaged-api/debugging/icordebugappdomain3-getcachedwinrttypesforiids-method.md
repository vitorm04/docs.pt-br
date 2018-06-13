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
ms.openlocfilehash: 7c8c82b3ace19d4b1d79fbfd296ce239e6da99ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409551"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
Obtém um enumerador para armazenada em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos em um domínio de aplicativo com base em seus identificadores de interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cReqTypes`  
 [in] O número de tipos necessários.  
  
 `iidsToResolve`  
 [in] Um ponteiro para uma matriz que contém os identificadores de interface correspondente para as representações gerenciadas do [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos a serem recuperados.  
  
 `ppTypesEnum`  
 [out] Um ponteiro para o endereço de um objeto de interface de "ICorDebugTypeEnum" que permite a enumeração de cache gerenciado representações do [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos recuperados com base em identificadores de interface `iidsToResolve`.  
  
## <a name="remarks"></a>Comentários  
 Se o método falhar recuperar informações de um identificador de interface específica, a entrada correspondente na coleção "ICorDebugTypeEnum" terá um tipo de `ELEMENT_TYPE_END` erros devido a problemas de recuperação de dados, ou `ELEMENT_TYPE_VOID` para interface desconhecida identificadores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugAppDomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
