---
title: Função _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776678"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_Função AxlPublicKeyBlobToPublicKeyToken
Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCspPublicKeyBlob`  
 [in] O blob da chave pública CSP.  
  
 `ppwszPublicKeyHash`  
 [out] Um ponteiro para WCHAR * para receber o hash da chave pública com codificação hexadecimal.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](index.md)
