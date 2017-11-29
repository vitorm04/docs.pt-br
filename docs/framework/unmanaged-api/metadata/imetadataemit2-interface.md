---
title: Interface IMetaDataEmit2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 235134c66395f04a87ed4f3325f5cc4cd9fecfc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2-interface"></a>Interface IMetaDataEmit2
Estende o [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalmente para oferecer a capacidade de trabalhar com tipos genéricos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Cria uma definição para um parâmetro de tipo genérico e obtém um token para esse parâmetro de tipo genérico.|  
|[Método DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Cria uma instância genérica de um método e recebe um token para a definição.|  
|[Método GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Obtém um valor que indica a diferença no tamanho dos dados que é necessário para expressar as alterações para a sessão atual de edit-and-continue.|  
|[Método ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Redefine o log de edit-and-continue e inicia uma nova sessão.|  
|[Método SaveDelta](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Salva as alterações da sessão atual edit-and-continue para o arquivo especificado.|  
|[Método SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Salva as alterações da sessão atual edit-and-continue na memória.|  
|[Método SaveDeltaToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Salva as alterações da sessão atual de editar e continuar o fluxo especificado.|  
|[Método SetGenericParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Define valores de propriedade para a definição de parâmetro genérico referenciado por token especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
