---
title: Interface IMetaDataImport2
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cd9d2cd2837ff43fbb266717546db3aa98190e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2-interface"></a>Interface IMetaDataImport2
Estende o [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para fornecer a capacidade de trabalhar com tipos genéricos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumGenericParamConstraints](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas com o parâmetro genérico representado pelo token especificado.|  
|[Método EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Obtém um enumerador para uma matriz de parâmetro genérico tokens associado com o TypeDef especificado ou MethodDef token.|  
|[Método EnumMethodSpecs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.|  
|[Método GetGenericParamConstraintProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Obtém os metadados associados com a restrição de parâmetro genérico representada pelo token de restrição especificada.|  
|[Método GetGenericParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.|  
|[Método GetMethodSpecProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Obtém a assinatura de metadados do método referenciado pelo MethodSpec especificado de token.|  
|[Método GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Obtém um valor que identifica a natureza do código em um PE (executável portátil) de arquivo, geralmente um arquivo DLL ou EXE, definido no escopo atual de metadados|  
|[Método GetVersionString](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.PortableExecutableKinds>  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
