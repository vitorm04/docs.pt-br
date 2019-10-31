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
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138681"
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
 fora Um `CONNID` que representa o identificador de conexão.  
  
## <a name="remarks"></a>Comentários  
 O método `GetConnectionID` retornará zero no parâmetro `pdwConnectionId`, se esse thread não fizer parte de uma conexão.  
  
 Se esse thread estiver conectado a uma instância do SSAS (Microsoft SQL Server 2005 Analysis Services), o `CONNID` será mapeado para um identificador de processo do servidor (SPID).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
