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
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442162"
---
# <a name="imetadataemitsethandler-method"></a>Método IMetaDataEmit::SetHandler
Define o método referenciado pelo ponteiro de `IUnknown` especificado como um retorno de chamada de notificação para remapeamentos de token.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pUnk`  
 no O manipulador a ser registrado.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de metadados envia a notificação usando o método fornecido pelo `SetHandler`, para compiladores que não geram registros de maneira otimizada e que gostaria de otimizar os registros salvos.  
  
 Se o método de retorno de chamada não for fornecido por meio de `SetHandler`, nenhuma otimização será executada no salvamento, exceto onde vários escopos de importação tiverem sido mesclados usando `IMapToken` na mesclagem para cada escopo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
