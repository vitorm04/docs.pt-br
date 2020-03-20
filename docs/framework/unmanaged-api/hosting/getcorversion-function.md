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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178184"
---
# <a name="getcorversion-function"></a>Função GetCORVersion
Retorna o número da versão do tempo de execução do idioma comum (CLR) que está sendo executado no processo atual.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>parâmetros  
 `pbuffer`  
 Um ponteiro para um buffer no qual o CLR retorna uma seqüência especificando a versão do tempo de execução que está atualmente carregado no processo. A seqüência retornada toma a mesma forma que as strings passadas para [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por exemplo, "v1.0.1216". Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações apropriadas do diretório para a versão mais recente do tempo de execução instalado no computador.  
  
 `cchBuffer`  
 O número de`WCHAR`caracteres (s) `pbuffer`que podem ser mantidos em .  
  
 `dwLength`  
 Um ponteiro para o número de `pbuffer`caracteres realmente retornado em . Se `pbuffer` for um ponteiro nulo, o tempo de execução retorna E_POINTER. Se o número de caracteres `pbuffer` for maior, então o comprimento de , o tempo de execução retorna ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
