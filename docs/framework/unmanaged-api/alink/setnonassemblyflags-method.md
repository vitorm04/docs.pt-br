---
title: Método SetNonAssemblyFlags
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8a22e958740b69ba0e09bf062bf4d86075c3ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777017"
---
# <a name="setnonassemblyflags-method"></a>Método SetNonAssemblyFlags
Define sinalizadores que não são específicos do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `afFlags`  
 Sinalizadores ALink.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
