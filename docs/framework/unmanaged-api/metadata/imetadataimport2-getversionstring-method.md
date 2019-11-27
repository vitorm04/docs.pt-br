---
title: Método IMetaDataImport2::GetVersionString
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 0c9f667edf30feb23e1cdaa28950503283fce42e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445230"
---
# <a name="imetadataimport2getversionstring-method"></a>Método IMetaDataImport2::GetVersionString
Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzBuf`  
 fora Uma matriz para armazenar a cadeia de caracteres que especifica a versão.  
  
 `ccBufSize`  
 no O tamanho, em caracteres largos, da matriz de `pwzBuf`.  
  
 `pccBufSize`  
 fora O número de caracteres largos, incluindo um terminador nulo, retornado na matriz de `pwzBuf`.  
  
## <a name="remarks"></a>Comentários  
 O método `GetVersionString` Obtém a versão interna do escopo de metadados atual. Se o escopo nunca tiver sido salvo, ele não terá uma versão interna e uma cadeia de caracteres vazia será retornada.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
