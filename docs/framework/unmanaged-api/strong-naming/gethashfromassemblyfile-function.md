---
title: Função GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f984d44d0a8acb85562a58653dfd2882053a0ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799281"
---
# <a name="gethashfromassemblyfile-function"></a>Função GetHashFromAssemblyFile
Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szFilePath`  
 no O caminho para o arquivo a ser transformado em hash.  
  
 `piHashAlg`  
 [entrada, saída] Uma constante que especifica o algoritmo de hash. Use zero para o algoritmo de hash padrão.  
  
 `pbHash`  
 fora O buffer de hash retornado.  
  
 `cchHash`  
 no O tamanho máximo solicitado de `pbHash`.  
  
 `pchHash`  
 fora O tamanho retornado, em bytes, de `pbHash`.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [Método GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
