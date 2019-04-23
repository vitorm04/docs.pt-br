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
ms.openlocfilehash: 4e549e13c0d51e4aa708a674a2224168ab66f8ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178159"
---
# <a name="nukedownloadedcache-function"></a>Função NukeDownloadedCache
Exclui o cache de download do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H.  
  
## <a name="remarks"></a>Comentários  
 O cache de download do CLR é a área em que os assemblies de nome forte que são baixados de uma URL são armazenados para possível reutilização.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** Fusion e mscorwks. dll. Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CreateHistoryReader](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [Função GetHistoryFileDirectory](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
