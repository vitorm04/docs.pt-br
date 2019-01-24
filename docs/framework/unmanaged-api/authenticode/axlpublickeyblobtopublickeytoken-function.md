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
ms.openlocfilehash: 2ac147596794f748d3160cdbd34b9f306dfdb379
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604412"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>Função _AxlPublicKeyBlobToPublicKeyToken
Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCspPublicKeyBlob`  
 [in] O blob da chave pública CSP.  
  
 `ppwszPublicKeyHash`  
 [out] Um ponteiro para WCHAR * para receber o hash da chave pública com codificação hexadecimal.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.  
  
## <a name="see-also"></a>Consulte também
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
