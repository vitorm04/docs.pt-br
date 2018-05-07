---
title: Authenticode (referência de API não gerenciada)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78149d1f8fdad3c11fe693221888f115af84ada2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referência de API não gerenciada)
Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função _AxlGetIssuerPublicKeyHash](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.  
  
 [Função _AxlPublicKeyBlobToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.  
  
 [Função _AxlRSAKeyValueToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 Converte um Módulo e um Expoente em um token de chave pública com nome forte.  
  
 [Função CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Função CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Função CertTimestampAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.  
  
 [Função CertVerifyAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 Verifica a validade de uma licença XrML Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 Define as informações sobre o signatário do Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 Define as informações sobre o carimbo de data/hora do Authenticode.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API não gerenciada](../../../../docs/framework/unmanaged-api/index.md)
