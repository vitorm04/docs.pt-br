---
title: Método IMetaDataImport::EnumTypeDefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20913d1cfa258036e8c20e826415f96a8984fdb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042478"
---
# <a name="imetadataimportenumtypedefs-method"></a>Método IMetaDataImport::EnumTypeDefs
Enumera os tokens de TypeDef que representa todos os tipos dentro do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out] Um ponteiro para o novo enumerador. Isso deve ser NULL para a primeira chamada desse método.  
  
 `rTypeDefs`  
 [in] A matriz usada para armazenar os tokens de TypeDef.  
  
 `cMax`  
 [in] O tamanho máximo da `rTypeDefs` matriz.  
  
 `pcTypeDefs`  
 [out] O número de tokens de TypeDef retornado no `rTypeDefs`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token para enumerar. Nesse caso, `pcTypeDefs` é zero.|  
  
## <a name="remarks"></a>Comentários  
 O token de TypeDef representa um tipo como uma classe ou uma interface, bem como qualquer tipo adicionado por meio de um mecanismo de extensibilidade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
