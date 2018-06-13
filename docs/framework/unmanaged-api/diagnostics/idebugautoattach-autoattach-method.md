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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c95423a6918da7cc043f8d46de13d166b8d895
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426179"
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
