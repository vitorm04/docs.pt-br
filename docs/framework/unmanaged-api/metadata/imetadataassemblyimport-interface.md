---
title: Interface IMetaDataAssemblyImport
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da75f98edb54080658dc86f48d4ebb458d72f20d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimport-interface"></a>Interface IMetaDataAssemblyImport
Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Libera o identificador para o enumerador especificado.|  
|[Método EnumAssemblyRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Obtém um ponteiro de interface para um enumerador que contém o `mdAssemblyRef` tokens dos assemblies referenciados pelo assembly no escopo atual de metadados.|  
|[Método EnumExportedTypes](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Obtém um ponteiro de interface para um enumerador que contém o `mdExportedType` tokens dos tipos COM referenciados pelo assembly no escopo atual de metadados.|  
|[Método EnumFiles](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Obtém um ponteiro de interface para um enumerador que contém o `mdFile` tokens dos arquivos referenciados pelo assembly no escopo atual de metadados.|  
|[Método EnumManifestResources](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Obtém um ponteiro de interface para um enumerador que contém o `mdManifestResource` tokens dos recursos referenciados pelo assembly no escopo atual de metadados.|  
|[Método FindAssembliesByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Obtém uma matriz de `mdAssemblyRef` tokens para os assemblies com o nome especificado.|  
|[Método FindExportedTypeByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Obtém um `mdExportedType` token para o tipo COM o nome especificado.|  
|[Método FindManifestResourceByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Obtém um `mdManifestResource` token para o recurso com o nome especificado.|  
|[Método GetAssemblyFromScope](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Obtém o token para o assembly no escopo atual de metadados.|  
|[Método GetAssemblyProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Obtém as configurações de propriedade do assembly especificado.|  
|[Método GetAssemblyRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Obtém as configurações de propriedade especificada `mdAssemblyRef` token.|  
|[Método GetExportedTypeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Obtém as configurações de propriedade do tipo especificado COM.|  
|[Método GetFileProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Obtém as configurações de propriedade do arquivo especificado.|  
|[Método GetManifestResourceProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Obtém as configurações de propriedade do recurso de manifesto especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
