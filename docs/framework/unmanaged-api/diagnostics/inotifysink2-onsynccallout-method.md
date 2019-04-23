---
title: Método INotifySink2::OnSyncCallOut
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf36b9e09f5e9eeb28930a6adc48426927a60e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145685"
---
# <a name="inotifysink2onsynccallout-method"></a>Método INotifySink2::OnSyncCallOut
É invocado quando uma chamada é horizontalmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `in_CallID`  
 [in] ID da chamada que for lançada. Ver [estrutura CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Buffer de chamada.  
  
 `out_pBufferSize`  
 [out] Tamanho do buffer de chamada, em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Consulte também

- [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Interface INotifySource2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interface INotifyConnection2](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
