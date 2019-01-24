---
title: Função _EFN_GetManagedObjectName
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eddb1461ad448a1a1718db8a11173e5e2e4a17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527777"
---
# <a name="efngetmanagedobjectname-function"></a>Função _EFN_GetManagedObjectName
Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Client`  
 [in] Um ponteiro para o cliente de depuração.  
  
 `objAddr`  
 [in] Um ponteiro de objeto gerenciado.  
  
 szName  
 [out] O nome do tipo.  
  
 `cbName`  
 [out] O número de caracteres disponíveis no buffer de cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retornará o HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0xa0 e um código de erro de 0x1000.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** SOS_Stacktrace.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
