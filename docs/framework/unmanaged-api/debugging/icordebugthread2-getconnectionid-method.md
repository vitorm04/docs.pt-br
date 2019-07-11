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
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768975"
---
# <a name="icordebugthread2getconnectionid-method"></a>Método ICorDebugThread2::GetConnectionID
Obtém o identificador de conexão para este objeto ICorDebugThread2.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwConnectionId`  
 [out] Um `CONNID` que representa o identificador de conexão.  
  
## <a name="remarks"></a>Comentários  
 O `GetConnectionID` método retorna zero no `pdwConnectionId` parâmetro, se esse thread não é parte de uma conexão.  
  
 Se esse thread está conectado a uma instância do Microsoft SQL Server 2005 Analysis Services (SSAS), o `CONNID` é mapeado para um identificador de processo do servidor (SPID).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
