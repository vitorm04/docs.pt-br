---
title: Função CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd77a8a81718837d55f3018564d0f4ba8fdc95ee
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080320"
---
# <a name="certtimestampauthenticodelicense-function"></a>Função CertTimestampAuthenticodeLicense
Carimbo de data/hora em uma licença Authenticode XrML.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSignedLicenseBlob`  
 [in] A licença Authenticode XrML assinada a receber o carimbo de data/hora. Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.  
  
 `pwszTimestampURI`  
 [in] O URI do servidor de carimbo de data/hora.  
  
 `pTimestampSignatureBlob`  
 [out] Um ponteiro para CRYPT_DATA_BLOB para receber a assinatura do carimbo de data/hora codificado por base64. É responsabilidade do chamador liberar `pTimestampSignatureBlob` -> `pbData` com `HepFree()` após o uso. Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.  
  
## <a name="remarks"></a>Comentários  
 A assinatura do carimbo de data/hora é, na realidade, uma mensagem PKCS #7 SignedData cujo conteúdo é o formulário binário do SignatureValue da assinatura da licença. Basicamente, isso funciona como uma referenda da licença.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
