---
title: Função GetCORSystemDirectory
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 008514e3637a980f3722d0c9896a17be33d54c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getcorsystemdirectory-function"></a>Função GetCORSystemDirectory
Retorna o diretório de instalação do common language runtime (CLR) que é carregado no processo. O diretório de instalação é totalmente qualificado, por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Esta função é preterida. Ele é substituído pelo [: Getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) método fornecido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbuffer`  
 [out] Um buffer no qual o tempo de execução retorna uma cadeia de caracteres que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução que é carregado no processo. Se o tempo de execução ainda não foi carregado no processo, a função retornará as informações de diretório apropriado para a versão mais recente do tempo de execução instalada no computador.  
  
 `cchBuffer`  
 [in] O tamanho, em bytes, de `pbuffer`.  
  
 `dwLength`  
 [out] O número de caracteres retornados em `pbuffer`.  
  
## <a name="remarks"></a>Comentários  
  
> [!CAUTION]
>  Não use essa função em processos que estão executando a versão 4 do CLR. Se uma versão anterior do CLR está instalada no computador, essa função retorna o diretório de instalação para essa versão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
