---
title: Método IManagedObject::GetObjectIdentity
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291246169a5cc2c95b117bc55bc269791885b2ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749108"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>Método IManagedObject::GetObjectIdentity
Obtém a identidade do objeto gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBSTRGUID`  
 [out] Um ponteiro para o GUID do processo no qual o objeto reside.  
  
 `AppDomainID`  
 [out] Um ponteiro para a ID do objeto domínio do aplicativo.  
  
 `pCCW`  
 [out] Um ponteiro para o índice do objeto no COM clássico tabela v.  
  
## <a name="remarks"></a>Comentários  
 A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio do aplicativo e o índice do objeto no COM clássica tabela v.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
