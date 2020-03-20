---
title: Método IMetaDataEmit::SetHandler
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177536"
---
# <a name="imetadataemitsethandler-method"></a>Método IMetaDataEmit::SetHandler
Define o método referenciado `IUnknown` pelo ponteiro especificado como um retorno de chamada de notificação para remapeamento de tokens.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pUnk`  
 [em] O manipulador para se registrar.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de metadados envia notificação usando `SetHandler`o método fornecido por , para compiladores que não geram registros de forma otimizada e que gostariam de otimizar registros salvos.  
  
 Se o método de retorno `SetHandler`de chamada não for fornecido através, nenhuma otimização será `IMapToken` realizada no save, exceto quando vários escopos de importação foram mesclados usando na mesclagem para cada escopo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
