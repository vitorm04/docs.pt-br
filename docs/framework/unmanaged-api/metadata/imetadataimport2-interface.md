---
title: Interface IMetaDataImport2
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429214"
---
# <a name="imetadataimport2-interface"></a>Interface IMetaDataImport2
Estende a interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) para fornecer a capacidade de trabalhar com tipos genéricos.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumGenericParamConstraints](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas ao parâmetro genérico representado pelo token especificado.|  
|[Método EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Obtém um enumerador para uma matriz de tokens de parâmetro genéricos associados ao TypeDef ou token MethodDef especificado.|  
|[Método EnumMethodSpecs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Obtém um enumerador para uma matriz de tokens de MethodSpec associados ao token MethodDef ou MemberRef especificado.|  
|[Método GetGenericParamConstraintProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Obtém os metadados associados à restrição de parâmetro genérico representada pelo token de restrição especificado.|  
|[Método GetGenericParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Obtém os metadados associados ao parâmetro genérico representado pelo token especificado.|  
|[Método GetMethodSpecProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Obtém a assinatura de metadados do método referenciado pelo token de MethodSpec especificado.|  
|[Método GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Obtém um valor que identifica a natureza do código em um arquivo executável portátil (PE), normalmente um arquivo DLL ou EXE, definido no escopo de metadados atual|  
|[Método GetVersionString](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
