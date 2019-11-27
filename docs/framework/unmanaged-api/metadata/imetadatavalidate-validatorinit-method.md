---
title: Método IMetaDataValidate::ValidatorInit
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 165a57d8029fe03b9de3754fcf7c4db757292cec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443603"
---
# <a name="imetadatavalidatevalidatorinit-method"></a>Método IMetaDataValidate::ValidatorInit
Define um sinalizador que especifica o tipo do módulo no escopo de metadados atual e registra o método de retorno de chamada especificado para erros de validação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwModule`  
 no Um valor da enumeração [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) que especifica o tipo do módulo no escopo de metadados atual.  
  
 `pUnk`  
 no Um ponteiro para uma instância [IUnknown](/cpp/atl/iunknown) que serve como um retorno de chamada de função para erros de validação.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataValidate](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
