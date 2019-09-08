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
ms.openlocfilehash: aaf76d4c3d0f5fb59aeb35fae7a7020ee97b74d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776482"
---
# <a name="certtimestampauthenticodelicense-function"></a>Função CertTimestampAuthenticodeLicense
Carimbo de data/hora em uma licença Authenticode XrML.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pSignedLicenseBlob`  
 [in] A licença Authenticode XrML assinada a receber o carimbo de data/hora. Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pwszTimestampURI`  
 [in] O URI do servidor de carimbo de data/hora.  
  
 `pTimestampSignatureBlob`  
 [out] Um ponteiro para CRYPT_DATA_BLOB para receber a assinatura do carimbo de data/hora codificado por base64. É `pTimestampSignatureBlob` responsabilidade do chamador gratuita -> `pbData` com `HepFree()` após o uso. Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
## <a name="remarks"></a>Comentários  
 A assinatura do carimbo de data/hora é, na realidade, uma mensagem PKCS #7 SignedData cujo conteúdo é o formulário binário do SignatureValue da assinatura da licença. Basicamente, isso funciona como uma referenda da licença.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](index.md)
