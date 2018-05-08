---
title: Função NukeDownloadedCache
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="nukedownloadedcache-function"></a>Função NukeDownloadedCache
Exclui o cache de download do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido no Winerror. H.  
  
## <a name="remarks"></a>Comentários  
 O cache de download do CLR é a área de armazenamento de assemblies de nomes fortes que são baixados de uma URL para possível reutilização.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** Fusion e arquivo Mscorwks.dll. Use Fusion em vez do arquivo Mscorwks.dll para garantir que você a versão correta do .NET Framework de destino.  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CreateHistoryReader](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [Função GetHistoryFileDirectory](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
