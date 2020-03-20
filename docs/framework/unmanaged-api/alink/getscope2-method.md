---
title: Método GetScope2
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179404"
---
# <a name="getscope2-method"></a>Método GetScope2
Obtém um escopo de importação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a>parâmetros  
 `AssemblyID`  
 ID da montagem do alvo.  
  
 `FileToken`  
 ID de arquivo a partir do qual importar.  
  
 `dwScope`  
 Escopo baseado em zero para importar.  
  
 `ppImportScope`  
 Recebe ponteiro para interface [IMetaDataImport2](../metadata/imetadataimport2-interface.md) para obter escopo indicado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método for bem sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Confira também

- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
