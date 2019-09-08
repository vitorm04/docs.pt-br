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
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="1d1e2-102">Authenticode (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1d1e2-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="1d1e2-103">Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d1e2-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1d1e2-104">In This Section</span></span>  
 [<span data-ttu-id="1d1e2-105">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="1d1e2-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="1d1e2-106">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="1d1e2-107">Função _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="1d1e2-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="1d1e2-108">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="1d1e2-109">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="1d1e2-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="1d1e2-110">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="1d1e2-111">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="1d1e2-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="1d1e2-112">Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="1d1e2-113">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="1d1e2-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="1d1e2-114">Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="1d1e2-115">Função CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="1d1e2-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="1d1e2-116">Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="1d1e2-117">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="1d1e2-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="1d1e2-118">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="1d1e2-119">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="1d1e2-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="1d1e2-120">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="1d1e2-121">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="1d1e2-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="1d1e2-122">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="1d1e2-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1e2-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d1e2-123">See also</span></span>

- [<span data-ttu-id="1d1e2-124">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="1d1e2-124">Unmanaged API Reference</span></span>](../index.md)
