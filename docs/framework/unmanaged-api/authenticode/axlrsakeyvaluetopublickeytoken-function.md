---
title: Função axlrsakeyvaluetopublickeytoken
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
ms.openlocfilehash: e09391af9b5d71cfa423b3bf1a2b307117d0dee1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517592"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>\_Função AxlRSAKeyValueToPublicKeyToken

Converte um Módulo e um Expoente em um token de chave pública com nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a>Parâmetros  
 `pModulusBlob`  
 [in] O blob de módulo codificado na base64 (da \<Modulus > elemento).  Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.  
  
 `pExponentBlob`  
 [in] O blob de expoente codificado de base64 (da \<expoente > elemento). Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.  
  
 `ppwszPublicKeyToken`  
 [out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
