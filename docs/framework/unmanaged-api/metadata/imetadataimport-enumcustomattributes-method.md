---
title: Método IMetaDataImport::EnumCustomAttributes
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196197"
---
# <a name="imetadataimportenumcustomattributes-method"></a>Método IMetaDataImport::EnumCustomAttributes
Enumera os tokens de definição de atributo personalizado associados com o tipo especificado ou um membro.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador retornado.  
  
 `tk`  
 [in] Um token para o escopo da enumeração, ou zero para todos os atributos personalizados.  
  
 `tkType`  
 [in] Um token para o construtor do tipo dos atributos a serem enumerados, ou `null` para todos os tipos.  
  
 `rCustomAttributes`  
 [out] Uma matriz de tokens de atributo personalizado.  
  
 `cMax`  
 [in] O tamanho máximo da `rCustomAttributes` matriz.  
  
 `pcCustomAttributes`  
 [out, opcional] O número real de valores do token retornado na `rCustomAttributes`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` retornado com êxito.|  
|`S_FALSE`|Não há nenhum atributo personalizado para enumerar. Nesse caso, `pcCustomAttributes` é zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
