---
title: Método IDebugAutoAttach::AutoAttach
ms.date: 03/30/2017
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
ms.openlocfilehash: 766aeb31436101babeab31b615a1c633578bfcc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445528"
---
# <a name="idebugautoattachautoattach-method"></a>Método IDebugAutoAttach::AutoAttach
Performs server-invoked debugger auto attach.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `guidPort`  
 [in] Always set to `GUID_NULL`.  
  
 `dwPid`  
 [in] Process ID, normally retrieved with the `GetCurrentProcessId` function.  
  
 `dwProgramType`  
 [in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.  
  
 `dwProgramId`  
 [in] Program ID.  
  
 `pszSessionId`  
 [in] String passed by the debug verb.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisitos  
 **Header:** DbgAutoAttach.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IDebugAutoAttach](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
