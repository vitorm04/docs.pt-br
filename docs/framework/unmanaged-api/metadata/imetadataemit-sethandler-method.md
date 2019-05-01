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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac0e5db4a87b49d631bad4411f03fae8c1199aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050019"
---
# <a name="imetadataemitsethandler-method"></a>Método IMetaDataEmit::SetHandler
Define o método referenciado pelo especificado `IUnknown` ponteiro como um retorno de chamada de notificação para remapeamentos de token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pUnk`  
 [in] O manipulador para registrar.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de metadados envia notificação por meio do método que é fornecido pelo `SetHandler`, para compiladores que não geram registros de forma otimizada e que gostaria de otimizar os registros salvos.  
  
 Se o método de retorno de chamada não é fornecido por meio `SetHandler`, sem otimização será executada no salvamento, exceto onde vários importar escopos foram mesclados usando `IMapToken` na mesclagem para cada escopo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
