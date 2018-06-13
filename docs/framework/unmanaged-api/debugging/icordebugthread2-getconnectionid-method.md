---
title: Método ICorDebugThread2::GetConnectionID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0e76b179854a380e66ac9daedffa8ccf4aa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422708"
---
# <a name="icordebugthread2getconnectionid-method"></a>Método ICorDebugThread2::GetConnectionID
Obtém o identificador de conexão para este objeto ICorDebugThread2.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwConnectionId`  
 [out] Um `CONNID` que representa o identificador de conexão.  
  
## <a name="remarks"></a>Comentários  
 O `GetConnectionID` método retorna zero no `pdwConnectionId` parâmetro, se esse thread não é parte de uma conexão.  
  
 Se esse thread está conectado a uma instância do Microsoft SQL Server 2005 Analysis Services (SSAS), o `CONNID` é mapeado para um identificador de processo do servidor (SPID).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
