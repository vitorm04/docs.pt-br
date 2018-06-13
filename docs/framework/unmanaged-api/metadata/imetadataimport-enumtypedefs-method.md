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
ms.openlocfilehash: 53ed486a885514d02bf2be9c473e102c2c5f0e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446837"
---
# <a name="imetadataimportenumtypedefs-method"></a>Método IMetaDataImport::EnumTypeDefs
Enumera os tokens de TypeDef que representa todos os tipos de dentro do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out] Um ponteiro para o novo enumerador. Isso deve ser NULL para a primeira chamada do método.  
  
 `rTypeDefs`  
 [in] A matriz usada para armazenar os tokens de TypeDef.  
  
 `cMax`  
 [in] O tamanho máximo da `rTypeDefs` matriz.  
  
 `pcTypeDefs`  
 [out] O número de tokens de TypeDef retornados em `rTypeDefs`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` retornou com êxito.|  
|`S_FALSE`|Não há nenhum tokens para enumerar. Nesse caso, `pcTypeDefs` é zero.|  
  
## <a name="remarks"></a>Comentários  
 O token de TypeDef representa um tipo como uma classe ou uma interface, bem como qualquer tipo adicionados por meio de um mecanismo de extensibilidade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
