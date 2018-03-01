---
title: "Função GetHistoryFileDirectory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a>Função GetHistoryFileDirectory
Recupera o caminho do diretório de histórico do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wzDir`  
 [out] Um buffer para armazenar o caminho para o diretório de histórico do aplicativo.  
  
 `pdwSize`  
 [out no] O comprimento do buffer.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido no arquivo de Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`wzDir`ou `pdwSize` é nulo ou a versão de cadeia de caracteres está incorreta.|  
  
## <a name="remarks"></a>Comentários  
 Após a conclusão bem-sucedida, o `pdwSize` argumento é definido como o comprimento da cadeia de caracteres de caminho.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** Fusion e arquivo Mscorwks.dll. Use Fusion em vez do arquivo Mscorwks.dll para garantir que você a versão correta do .NET Framework de destino.  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CreateHistoryReader](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [Função NukeDownloadedCache](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
