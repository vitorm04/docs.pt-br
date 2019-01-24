---
title: Função CoInitializeCor
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 438f2f58a4ce61d1757238fc46674611e4d677dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508529"
---
# <a name="coinitializecor-function"></a>Função CoInitializeCor
`CoInitializeCor` é obsoleto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a>Comentários  
 Para inicializar o common language runtime, use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** Cor.h  
  
## <a name="see-also"></a>Consulte também
- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
