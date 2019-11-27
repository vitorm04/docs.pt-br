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
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436313"
---
# <a name="imetadataassemblyimport-interface"></a>Interface IMetaDataAssemblyImport
Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Libera o identificador para o enumerador especificado.|  
|[Método EnumAssemblyRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Obtém um ponteiro de interface para um enumerador que contém os tokens de `mdAssemblyRef` dos assemblies referenciados pelo assembly no escopo de metadados atual.|  
|[Método EnumExportedTypes](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Obtém um ponteiro de interface para um enumerador que contém os tokens de `mdExportedType` dos tipos COM referenciados pelo assembly no escopo de metadados atual.|  
|[Método EnumFiles](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Obtém um ponteiro de interface para um enumerador que contém os tokens de `mdFile` dos arquivos referenciados pelo assembly no escopo de metadados atual.|  
|[Método EnumManifestResources](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Obtém um ponteiro de interface para um enumerador que contém os tokens de `mdManifestResource` dos recursos referenciados pelo assembly no escopo de metadados atual.|  
|[Método FindAssembliesByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Obtém uma matriz de tokens de `mdAssemblyRef` para os assemblies com o nome especificado.|  
|[Método FindExportedTypeByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Obtém um token de `mdExportedType` para o tipo com com o nome especificado.|  
|[Método FindManifestResourceByName](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Obtém um token de `mdManifestResource` para o recurso com o nome especificado.|  
|[Método GetAssemblyFromScope](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Obtém o token para o assembly no escopo de metadados atual.|  
|[Método GetAssemblyProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Obtém as configurações de Propriedade do assembly especificado.|  
|[Método GetAssemblyRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Obtém as configurações de Propriedade do token de `mdAssemblyRef` especificado.|  
|[Método GetExportedTypeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Obtém as configurações de Propriedade do tipo COM especificado.|  
|[Método GetFileProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Obtém as configurações de Propriedade do arquivo especificado.|  
|[Método GetManifestResourceProps](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Obtém as configurações de Propriedade do recurso de manifesto especificado.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
