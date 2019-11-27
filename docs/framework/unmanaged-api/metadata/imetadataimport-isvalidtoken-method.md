---
title: Método IMetaDataImport::IsValidToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: edf24de8ae38aab97e41a53cc86ae5aa6c592c50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434695"
---
# <a name="imetadataimportisvalidtoken-method"></a>Método IMetaDataImport::IsValidToken
Obtém um valor que indica se o token especificado contém uma referência válida a um objeto de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 no O token para verificar a validade de referência.  
  
## <a name="return-value"></a>Valor retornado  
 `true` se `tk` é um token de metadados válido dentro do escopo atual. Caso contrário, `false`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
