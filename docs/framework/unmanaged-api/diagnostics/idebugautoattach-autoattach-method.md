---
title: "Método IDebugAutoAttach::AutoAttach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b875fec2fdb6ecaeaccf8e58030b2fccbb8653b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugautoattachautoattach-method"></a>Método IDebugAutoAttach::AutoAttach
Executa automaticamente do servidor chamado depurador anexar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidPort`  
 [in] Sempre definido como `GUID_NULL`.  
  
 `dwPid`  
 [in] Processar ID, normalmente é recuperado com o `GetCurrentProcessId` função.  
  
 `dwProgramType`  
 [in] Tipo de programa: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, ou `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] ID do programa.  
  
 `pszSessionId`  
 [in] Cadeia de caracteres passada, o verbo debug.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugAutoAttach](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
