---
title: "Método ICorDebugFrame::GetStackRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a>Método ICorDebugFrame::GetStackRange
Obtém o intervalo de endereços absolutos deste quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStart`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilhas representado por esse `ICorDebugFrame` objeto.  
  
 `pEnd`  
 [out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilhas representado por esse `ICorDebugFrame` objeto.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de endereços da pilha é útil para juntando rastreamentos de pilha intercalada coletados a partir de vários mecanismos de depuração. O intervalo numérico não fornece nenhuma informação sobre o conteúdo do quadro de pilhas. Faz sentido somente para comparação de locais de quadro de pilha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
