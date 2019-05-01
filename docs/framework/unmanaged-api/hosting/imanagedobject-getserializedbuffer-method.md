---
title: Método IManagedObject::GetSerializedBuffer
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb9242160b684b3c7b90756d7b20811ad162fc30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043622"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>Método IManagedObject::GetSerializedBuffer
Obtém a representação de cadeia de caracteres desse objeto gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBSTR`  
 [out] Um ponteiro para uma cadeia de caracteres que é o objeto serializado.  
  
## <a name="remarks"></a>Comentários  
 O `GetSerializedBuffer` método serializa o objeto para que ele pode ser empacotado para o cliente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
