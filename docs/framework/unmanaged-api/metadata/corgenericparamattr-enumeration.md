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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d56be8c6f224010da22803894524299c0d376ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443524"
---
# <a name="corgenericparamattr-enumeration"></a>Enumeração CorGenericParamAttr
Contém valores que descrevem o <xref:System.Type> parâmetros para tipos genéricos, como usado em chamadas para [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`gpVarianceMask`|Variação de parâmetro só se aplica a parâmetros genéricos para interfaces e delegados.|  
|`gpNonVariant`|Indica a ausência de variação.|  
|`gpCovariant`|Indica a covariância.|  
|`gpContravariant`|Indica contravariância.|  
|`gpSpecialConstraintMask`|Restrições especiais podem aplicar a qualquer <xref:System.Type> parâmetro.|  
|`gpNoSpecialConstraint`|Indica que nenhuma restrição se aplica ao <xref:System.Type> parâmetro.|  
|`gpReferenceTypeConstraint`|Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.|  
|`gpNotNullableValueTypeConstraint`|Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor não pode ser um valor nulo.|  
|`gpDefaultConstructorConstraint`|Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não usa nenhum parâmetro.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
