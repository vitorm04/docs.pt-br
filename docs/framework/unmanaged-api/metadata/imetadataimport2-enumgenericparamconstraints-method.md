---
title: Método IMetaDataImport2::EnumGenericParamConstraints
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd5d35cb13bb55fc73e160089cbc1050cb3d5c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449212"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>Método IMetaDataImport2::EnumGenericParamConstraints
Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas com o parâmetro genérico representado pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [out no] Um ponteiro para o enumerador.  
  
 `tk`  
 [in]   Um token que representa o parâmetro genérico cujas restrições devem ser enumerados.  
  
 `rGenericParamConstraints`  
 [out] A matriz de restrições de parâmetro genérico para enumerar.  
  
 `cMax`  
 [in]   O número máximo solicitado de tokens para colocar em `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] Um ponteiro para o número de tokens são colocados em `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` retornou com êxito.|  
|`S_FALSE`|`phEnum` não tem nenhum elemento de membro. Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
