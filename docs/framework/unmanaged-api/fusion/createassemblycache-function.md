---
title: "Função CreateAssemblyCache"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyCache
helpviewer_keywords: CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b6dfc8cd90b5a37b82b26d4f8e494159dc1fd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblycache-function"></a>Função CreateAssemblyCache
Obtém um ponteiro para um novo [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instância que representa o cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppAsmCache`  
 [out] Retornado `IAssemblyCache` ponteiro.  
  
 `dwReserved`  
 [in] Reservado para extensibilidade futura. `dwReserved`deve ser 0 (zero).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
