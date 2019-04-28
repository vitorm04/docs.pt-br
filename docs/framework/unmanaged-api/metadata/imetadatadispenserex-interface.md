---
title: Interface IMetaDataDispenserEx
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992596"
---
# <a name="imetadatadispenserex-interface"></a>Interface IMetaDataDispenserEx
Estende o [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface para fornecer a capacidade de controlar como as APIs de metadados operam no escopo atual de metadados.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método FindAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Este método não está implementado. Se chamado, ele retornará E_NOTIMPL.|  
|[Método FindAssemblyModule](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Este método não está implementado. Se chamado, ele retornará E_NOTIMPL.|  
|[Método GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Obtém o diretório que mantém o atual common language runtime (CLR). Esse método tem suporte apenas para uso por depuradores out-of-process. Se chamado de outro componente, ele retornará E_NOTIMPL.|  
|[Método GetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Obtém o valor da opção especificada para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atual são tratadas.|  
|[Método OpenScopeOnITypeInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Este método não está implementado. Se chamado, ele retornará E_NOTIMPL.|  
|[Método SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Define a opção especificada para um determinado valor para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atual são tratadas.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
