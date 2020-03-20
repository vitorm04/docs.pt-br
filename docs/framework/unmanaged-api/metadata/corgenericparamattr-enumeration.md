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
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176169"
---
# <a name="corgenericparamattr-enumeration"></a>Enumeração CorGenericParamAttr
Contém valores <xref:System.Type> que descrevem os parâmetros para tipos genéricos, como usado em chamadas para [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
  
|Membro|Descrição|  
|------------|-----------------|  
|`gpVarianceMask`|A variância de parâmetros se aplica apenas a parâmetros genéricos para interfaces e delegados.|  
|`gpNonVariant`|Indica a ausência de variância.|  
|`gpCovariant`|Indica covariância.|  
|`gpContravariant`|Indica contravariância.|  
|`gpSpecialConstraintMask`|Restrições especiais podem <xref:System.Type> ser aplicadas a qualquer parâmetro.|  
|`gpNoSpecialConstraint`|Indica que nenhuma restrição <xref:System.Type> se aplica ao parâmetro.|  
|`gpReferenceTypeConstraint`|Indica que <xref:System.Type> o parâmetro deve ser um tipo de referência.|  
|`gpNotNullableValueTypeConstraint`|Indica que <xref:System.Type> o parâmetro deve ser um tipo de valor que não pode ser um valor nulo.|  
|`gpDefaultConstructorConstraint`|Indica que <xref:System.Type> o parâmetro deve ter um construtor público padrão que não tenha parâmetros.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
