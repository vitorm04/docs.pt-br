---
title: Função CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099737"
---
# <a name="certverifyauthenticodelicense-function"></a>Função CertVerifyAuthenticodeLicense
Verifica a validade de uma licença XrML Authenticode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pLicenseBlob`  
 [In] A licença XrML Authenticode a ser verificada.  
  
 Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `dwFlags`  
 [in] Opcional. Uma combinação dos seguintes valores:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [out] Para receber informações do assinante. Se a licença não foi assinada, `dwError` é definido como TRUST_E_NOSIGNATURE. É responsabilidade do chamador liberar recursos usando a função [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) após o uso.  
  
 Consulte [estrutura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [out] Para receber informações do carimbo de hora, se disponível. Se a licença não recebeu carimbo de hora, `dwError` é definido como TRUST_E_NOSIGNATURE. É responsabilidade do chamador liberar recursos usando a função [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) após o uso.  
  
 Consulte [estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se houver êxito. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](index.md)
- [Método GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
