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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08c4a97b8cbc61a735bb9c1e6a31a698e7eefc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787352"
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
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly de destino.  
  
 `FileToken`  
 ID do arquivo do qual importar.  
  
 `dwScope`  
 Escopo de base zero para importar.  
  
 `ppImportScope`  
 Recebe o ponteiro para a interface de [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) para o escopo indicado.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
