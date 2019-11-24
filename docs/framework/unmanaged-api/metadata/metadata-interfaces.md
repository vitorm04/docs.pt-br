---
title: Interfaces de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431593"
---
# <a name="metadata-interfaces"></a>Interfaces de metadados
This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Provides methods for dynamic code compilation.  
  
 [Interface IHostFilter](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Provides a method for the run-time host to mark metadata tokens for processing.  
  
 [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Provides mapping capabilities between imported and emitted metadata signatures.  
  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.  
  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Provides methods to access and examine the contents of an assembly manifest.  
  
 [Interface IMetaDataConverter](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.  
  
 [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` é obsoleto. Use `IMetaDataDispenserEx` em seu lugar.  
  
 [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Provides methods that map areas of memory for creating or modifying metadata.  
  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Provides methods to create, modify and store metadata about the assembly in the currently defined scope.  
  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.  
  
 [Interface IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.  
  
 [Interface IMetaDataFilter](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.  
  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Provides methods for importing and manipulating types from other assemblies.  
  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Extends `IMetaDataImport` to provide the capability of working with generic types.  
  
 [Interface IMetaDataInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Provides a method that gets information about the mapping of metadata from an on-disk file into memory.  
  
 [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Provides methods for the storage and retrieval of metadata information in tables.  
  
 [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Extends `IMetaDataTables` to include methods for working with metadata streams.  
  
 [Interface IMetaDataValidate](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Provides methods to use for validation of metadata signatures.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Uniões de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
