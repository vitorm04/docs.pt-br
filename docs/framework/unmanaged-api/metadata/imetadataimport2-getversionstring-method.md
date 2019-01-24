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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e041efed929255d4ce3af2d051a391bc4179cda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630912"
---
# <a name="imetadataimport2getversionstring-method"></a>Método IMetaDataImport2::GetVersionString
Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzBuf`  
 [out] Uma matriz para armazenar a cadeia de caracteres que especifica a versão.  
  
 `ccBufSize`  
 [in] O tamanho, em caracteres largos, da `pwzBuf` matriz.  
  
 `pccBufSize`  
 [out] O número de caracteres largos, incluindo um terminador nulo, retornado no `pwzBuf` matriz.  
  
## <a name="remarks"></a>Comentários  
 O `GetVersionString` método obtém a versão criada do escopo de metadados atual. Se o escopo nunca tiver sido salvo, ele não terá uma versão criada para e uma cadeia de caracteres vazia será retornada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
