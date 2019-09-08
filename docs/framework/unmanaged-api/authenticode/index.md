---
title: Authenticode (referência de API não gerenciada)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2c0163d03a19a7bc00ae705fd633ef4f0880082
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776564"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referência de API não gerenciada)
Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.  
  
 [Função _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.  
  
 [Função _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Converte um Módulo e um Expoente em um token de chave pública com nome forte.  
  
 [Função CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Função CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Função CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.  
  
 [Função CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Verifica a validade de uma licença XrML Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Define as informações sobre o signatário do Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Define as informações sobre o carimbo de data/hora do Authenticode.  
  
## <a name="see-also"></a>Consulte também

- [Referência de API não gerenciada](../index.md)
