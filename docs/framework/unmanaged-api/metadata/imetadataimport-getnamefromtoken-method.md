---
title: Método IMetaDataImport::GetNameFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d77891478c9136a18dc4c9c44beed805244dd1a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225931"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>Método IMetaDataImport::GetNameFromToken
Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado. Esse método é obsoleto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tk`  
 [in] O token que representa o objeto para retornar o nome para o.  
  
 `pszUtf8NamePtr`  
 [out] Um ponteiro para o nome do objeto UTF-8 no heap.  
  
## <a name="remarks"></a>Comentários  
 `GetNameFromToken` é obsoleto. Como alternativa, chamar um método para obter as propriedades de um determinado tipo de token necessário, como `GetFieldProps` para um campo ou `GetMethodProps` para um método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET framework:** 1.0  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
