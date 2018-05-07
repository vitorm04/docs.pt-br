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
ms.openlocfilehash: f1975e5bf20453a3bcd6761d9734be7ddd2ceef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imanagedobjectgetobjectidentity-method"></a>Método IManagedObject::GetObjectIdentity
Obtém a identidade do objeto gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBSTRGUID`  
 [out] Um ponteiro para o GUID do processo no qual o objeto reside.  
  
 `AppDomainID`  
 [out] Um ponteiro para a ID de domínio de aplicativo do objeto.  
  
 `pCCW`  
 [out] Um ponteiro para o índice do objeto do COM clássico tabela v.  
  
## <a name="remarks"></a>Comentários  
 A identidade de um objeto gerenciado inclui o GUID do processo, ID de domínio de aplicativo e o índice do objeto da COM clássica tabela v.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
