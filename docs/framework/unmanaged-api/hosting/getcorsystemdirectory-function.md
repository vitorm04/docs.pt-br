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
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178201"
---
# <a name="getcorsystemdirectory-function"></a>Função GetCORSystemDirectory
Retorna o diretório de instalação do tempo de execução de linguagem comum (CLR) que é carregado no processo. O diretório de instalação é totalmente qualificado, por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Esta função é preterida. Ele é substituído pelo método [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) fornecido no .NET Framework 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>parâmetros  
 `pbuffer`  
 [fora] Um buffer no qual o tempo de execução retorna uma seqüência que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução que é carregado no processo. Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações apropriadas do diretório para a versão mais recente do tempo de execução instalado no computador.  
  
 `cchBuffer`  
 [em] O tamanho, em bytes, de `pbuffer`.  
  
 `dwLength`  
 [fora] O número de caracteres retornou em `pbuffer`.  
  
## <a name="remarks"></a>Comentários  
  
> [!CAUTION]
> Não use esta função em processos que estão em execução versão 4 da CLR. Se uma versão anterior do CLR estiver instalada no computador, esta função reameda o diretório de instalação dessa versão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
