---
title: Método CloseEnum
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 018af6929ad4023c70bfb975b9be010912415dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446566"
---
# <a name="closeenum-method"></a>Método CloseEnum
Closes the indicated enumeration and frees associated resources.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hEnum`  
 Handle of enumeration to be closed.  
  
## <a name="return-value"></a>Valor retornado  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Requisitos  
 Requires alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
