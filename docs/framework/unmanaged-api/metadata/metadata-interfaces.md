---
title: Interfaces de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a704d531b1c49ffe653009e0e90f33b7a126e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-interfaces"></a>Interfaces de metadados
Esta seção descreve as interfaces não gerenciadas que fornecem acesso aos metadados expostos por tipos do .NET Framework, métodos, campos e assim por diante.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Fornece métodos para compilação de código dinâmico.  
  
 [Interface IHostFilter](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Fornece um método para o host de tempo de execução marcar os tokens de metadados para processamento.  
  
 [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Fornece recursos de mapeamento entre importados e emitidos assinaturas de metadados.  
  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Fornece métodos que suportam o modelo de descrição Self usado pelo common language runtime (CLR) para resolver e consomem recursos.  
  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.  
  
 [Interface IMetaDataConverter](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Fornece métodos para mapear as bibliotecas de tipo para suas assinaturas de metadados e para converter de um ao outro.  
  
 [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` é obsoleto. Use `IMetaDataDispenserEx` em seu lugar.  
  
 [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Fornece métodos que mapeiam as áreas de memória para criação ou modificação de metadados.  
  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Fornece métodos para criar, modificar e armazenar os metadados sobre o assembly no escopo definido no momento.  
  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Fornece métodos para definir e modificar as assinaturas de metadados de métodos e construtores com parâmetros de tipo <xref:System.Type?displayProperty=nameWithType>.  
  
 [Interface IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Fornece um mecanismo de retorno de chamada para o relatório de erros durante a resolução da assinatura de metadados para um assembly.  
  
 [Interface IMetaDataFilter](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Fornece métodos para a marcação e a filtragem de tokens de metadados para evitar a repetição de ações que já foi usadas.  
  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Fornece métodos para importação e manipulação de tipos de outros assemblies.  
  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Estende `IMetaDataImport` para fornecer a capacidade de trabalhar com tipos genéricos.  
  
 [Interface IMetaDataInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Fornece um método que obtém informações sobre o mapeamento de metadados de um arquivo em disco na memória.  
  
 [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Fornece métodos para o armazenamento e recuperação de informações de metadados nas tabelas.  
  
 [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Estende `IMetaDataTables` para incluir os métodos para trabalhar com fluxos de metadados.  
  
 [Interface IMetaDataValidate](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Fornece métodos para usar para validação de assinaturas de metadados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Uniões de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
