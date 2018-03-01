---
title: "Método IMetaDataImport2::EnumGenericParamConstraints"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
|`S_OK`|`EnumGenericParameterConstraints`retornou com êxito.|  
|`S_FALSE`|`phEnum`não tem nenhum elemento de membro. Nesse caso, `pcGenericParameterConstraints` é definido como 0 (zero).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
