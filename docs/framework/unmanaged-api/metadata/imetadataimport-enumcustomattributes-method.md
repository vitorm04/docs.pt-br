---
title: "Método IMetaDataImport::EnumCustomAttributes"
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
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e45c15f3d09972d1c83c9b330965c4e8afd21b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumcustomattributes-method"></a>Método IMetaDataImport::EnumCustomAttributes
Enumera os tokens de definição de atributo personalizado associados ao tipo especificado ou membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out no] Um ponteiro para o enumerador retornado.  
  
 `tk`  
 [in] Um token para o escopo de enumeração ou zero para todos os atributos personalizados.  
  
 `tkType`  
 [in] Um token para o construtor do tipo de atributos a serem enumerados, ou `null` para todos os tipos.  
  
 `rCustomAttributes`  
 [out] Uma matriz de tokens de atributo personalizado.  
  
 `cMax`  
 [in] O tamanho máximo da `rCustomAttributes` matriz.  
  
 `pcCustomAttributes`  
 [out, opcional] O número real de valores do token retornado na `rCustomAttributes`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`retornou com êxito.|  
|`S_FALSE`|Não há nenhum atributo personalizado para enumerar. Nesse caso, `pcCustomAttributes` é zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
