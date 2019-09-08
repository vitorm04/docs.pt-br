---
title: Função _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690035ffe0724d3987a198c78bf14e668527b98a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787026"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_Função AxlRSAKeyValueToPublicKeyToken

Converte um Módulo e um Expoente em um token de chave pública com nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pModulusBlob`  
 no O blob de módulo codificado em Base64 (no \<elemento > do módulo).  Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pExponentBlob`  
 no O blob de expoente codificado em Base64 (do \<elemento > exponencial). Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyToken`  
 [out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](index.md)
