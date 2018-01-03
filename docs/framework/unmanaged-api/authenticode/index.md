---
title: "Authenticode (referência de API não gerenciada)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b790064ef64ab44f3798a62d5dbf004f0f0bba6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="2e68b-102">Authenticode (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2e68b-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="2e68b-103">Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.</span><span class="sxs-lookup"><span data-stu-id="2e68b-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e68b-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2e68b-104">In This Section</span></span>  
 [<span data-ttu-id="2e68b-105">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="2e68b-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="2e68b-106">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="2e68b-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="2e68b-107">Função _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="2e68b-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="2e68b-108">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="2e68b-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="2e68b-109">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="2e68b-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="2e68b-110">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="2e68b-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="2e68b-111">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="2e68b-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="2e68b-112">Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="2e68b-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="2e68b-113">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="2e68b-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="2e68b-114">Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="2e68b-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="2e68b-115">Função CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="2e68b-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="2e68b-116">Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="2e68b-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="2e68b-117">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="2e68b-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="2e68b-118">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2e68b-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="2e68b-119">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="2e68b-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="2e68b-120">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2e68b-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="2e68b-121">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="2e68b-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="2e68b-122">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2e68b-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e68b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e68b-123">See Also</span></span>  
 [<span data-ttu-id="2e68b-124">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="2e68b-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
