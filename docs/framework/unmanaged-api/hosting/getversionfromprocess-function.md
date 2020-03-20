---
title: Função GetVersionFromProcess
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178126"
---
# <a name="getversionfromprocess-function"></a>Função GetVersionFromProcess
Obtém o número da versão do tempo de execução do idioma comum (CLR) que está associado à alça de processo especificada.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `hProcess`  
 [em] Uma alça para um processo.  
  
 `pVersion`  
 [fora] Um buffer que contém a seqüência de números da versão após a conclusão bem sucedida do método.  
  
 `cchBuffer`  
 [em] O comprimento do buffer da versão.  
  
 `pdwLength`  
 [fora] Um ponteiro para o comprimento da seqüência numérica da versão.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com sucesso.|  
|E_INVALIDARG|`pVersion`é nulo e `cchBuffer` não é nulo, ou vice-versa.<br /><br /> -ou-<br /><br /> `hProcess`não é uma alça válida para um processo.<br /><br /> -ou-<br /><br /> A CLR não está carregada.|  
|Error_insufficient_buffer|`cchBuffer`é nulo ou menor do que o comprimento da seqüência de versão.|  
|E_NOTIMPL|Este método não está disponível no sistema operacional Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [Função GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
