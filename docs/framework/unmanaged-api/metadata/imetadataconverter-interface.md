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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008372"
---
# <a name="imetadataconverter-interface"></a>Interface IMetaDataConverter
Fornece métodos para mapear bibliotecas de tipos para suas assinaturas de metadados e para converter de uma para a outra.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetMetaDataFromTypeInfo](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Obtém um ponteiro para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados para a biblioteca de tipos referenciada pela `ITypeInfo` instância especificada.|  
|[Método GetMetaDataFromTypeLib](imetadataconverter-getmetadatafromtypelib-method.md)|Obtém um ponteiro para uma `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pela `ITypeLib` instância especificada.|  
|[Método GetTypeLibFromMetaData](imetadataconverter-gettypelibfrommetadata-method.md)|Obtém um ponteiro para uma `ITypeLib` instância que representa a biblioteca de tipos que tem o módulo e os nomes de biblioteca especificados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interfaces de metadados](metadata-interfaces.md)
- [Interface IMetaDataImport](imetadataimport-interface.md)
