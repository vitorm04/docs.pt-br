---
title: Interface IMetaDataConverter
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29709a4297d53cc5e40daf732ac89751ead95152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataconverter-interface"></a>Interface IMetaDataConverter
Fornece métodos para mapear as bibliotecas de tipo para suas assinaturas de metadados e para converter de um ao outro.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetMetaDataFromTypeInfo](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Obtém um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instância que representa a assinatura de metadados para a biblioteca de tipos referenciada por especificado `ITypeInfo` instância.|  
|[Método GetMetaDataFromTypeLib](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|Obtém um ponteiro para um `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pelo `ITypeLib` instância.|  
|[Método GetTypeLibFromMetaData](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de módulo e a biblioteca especificados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
