---
title: Função GetCORVersion
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd398a5b214ac0046d5fe1965f70eef2eedaa6b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490393"
---
# <a name="getcorversion-function"></a>Função GetCORVersion
Retorna o número de versão do common language runtime (CLR) que está em execução no processo atual.  
  
 Essa função foi preterida no .NET Framework 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbuffer`  
 Um ponteiro para um buffer no qual o CLR retorna uma cadeia de caracteres que especifica a versão do tempo de execução que atualmente é carregado no processo. A cadeia de caracteres retornada usa a mesma forma como cadeias de caracteres passados para [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por exemplo, "v1.0.1216". Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações de diretório apropriado para a versão mais recente do tempo de execução instalado no computador.  
  
 `cchBuffer`  
 O número de caracteres (`WCHAR`s) que podem ser mantidos em `pbuffer`.  
  
 `dwLength`  
 Um ponteiro para o número de caracteres retornado de fato no `pbuffer`. Se `pbuffer` for um ponteiro nulo, o tempo de execução retorna E_POINTER. Se o número de caracteres for maior, em seguida, o comprimento de `pbuffer` , o tempo de execução retorna ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
