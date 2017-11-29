---
title: "Função GetCORVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORVersion
helpviewer_keywords: GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6218714030892531f3b9ed4b4a79917347d250db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getcorversion-function"></a>Função GetCORVersion
Retorna o número de versão do common language runtime (CLR) que está em execução no processo atual.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbuffer`  
 Um ponteiro para um buffer no qual o CLR retorna uma cadeia de caracteres que especifica a versão do tempo de execução que está atualmente carregada no processo. A cadeia de caracteres retornada assume o mesmo formato, como cadeias de caracteres passados para [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por exemplo, "v1.0.1216". Se o tempo de execução ainda não foi carregado no processo, a função retornará as informações de diretório apropriado para a versão mais recente do tempo de execução instalada no computador.  
  
 `cchBuffer`  
 O número de caracteres (`WCHAR`s) que pode ser mantido em `pbuffer`.  
  
 `dwLength`  
 Um ponteiro para o número de caracteres de fato retornadas em `pbuffer`. Se `pbuffer` é um ponteiro nulo, o tempo de execução retorna E_POINTER. Se o número de caracteres for maior, em seguida, o comprimento de `pbuffer` , o tempo de execução retorna ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
