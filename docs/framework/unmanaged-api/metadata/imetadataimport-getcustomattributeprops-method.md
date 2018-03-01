---
title: "Método IMetaDataImport::GetCustomAttributeProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1e6ef9443b99b3e6b36154558ce226d421dbc0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>Método IMetaDataImport::GetCustomAttributeProps
Obtém o valor do atributo personalizado, dado seu token de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cv`  
 [in] Um token de metadados que representa o atributo personalizado a ser recuperado.  
  
 `ptkObj`  
 [out, opcional] Um token de metadados que representa o objeto que modifica o atributo personalizado. Esse valor pode ser qualquer tipo de token de metadados exceto `mdCustomAttribute`.  
  
 `ptkType`  
 [out, opcional] Um `mdMethodDef` ou `mdMemberRef` metadados token representando o <xref:System.Type> do atributo personalizado retornado.  
  
 `ppBlob`  
 [out, opcional] Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.  
  
 `pcbSize`  
 [out, opcional] O tamanho em bytes dos dados retornados em *`ppBlob`.  
  
## <a name="remarks"></a>Comentários  
 Um atributo personalizado é armazenado como uma matriz de dados, o formato que é entendido pelo mecanismo de metadados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
