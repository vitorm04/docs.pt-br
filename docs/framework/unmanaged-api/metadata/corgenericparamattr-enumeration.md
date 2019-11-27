---
title: Enumeração CorGenericParamAttr
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450283"
---
# <a name="corgenericparamattr-enumeration"></a>Enumeração CorGenericParamAttr
Contém valores que descrevem os parâmetros de <xref:System.Type> para tipos genéricos, conforme usado em chamadas para [IMetaDataEmit2::D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`gpVarianceMask`|A variação de parâmetro aplica-se somente a parâmetros genéricos para interfaces e delegados.|  
|`gpNonVariant`|Indica a ausência de variação.|  
|`gpCovariant`|Indica covariância.|  
|`gpContravariant`|Indica contravariância.|  
|`gpSpecialConstraintMask`|Restrições especiais podem ser aplicadas a qualquer parâmetro de <xref:System.Type>.|  
|`gpNoSpecialConstraint`|Indica que nenhuma restrição se aplica ao parâmetro <xref:System.Type>.|  
|`gpReferenceTypeConstraint`|Indica que o parâmetro de <xref:System.Type> deve ser um tipo de referência.|  
|`gpNotNullableValueTypeConstraint`|Indica que o parâmetro de <xref:System.Type> deve ser um tipo de valor que não pode ser um valor nulo.|  
|`gpDefaultConstructorConstraint`|Indica que o parâmetro <xref:System.Type> deve ter um construtor público padrão que não aceite parâmetros.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
