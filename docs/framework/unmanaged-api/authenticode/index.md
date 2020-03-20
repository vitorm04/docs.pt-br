---
title: Authenticode (referência de API não gerenciada)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132463"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="bbf27-102">Authenticode (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bbf27-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="bbf27-103">Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.</span><span class="sxs-lookup"><span data-stu-id="bbf27-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbf27-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bbf27-104">In This Section</span></span>  
 [<span data-ttu-id="bbf27-105">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="bbf27-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="bbf27-106">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="bbf27-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="bbf27-107">Função _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="bbf27-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="bbf27-108">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="bbf27-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="bbf27-109">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="bbf27-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="bbf27-110">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="bbf27-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="bbf27-111">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="bbf27-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="bbf27-112">Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="bbf27-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="bbf27-113">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="bbf27-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="bbf27-114">Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="bbf27-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="bbf27-115">Função CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="bbf27-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="bbf27-116">Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="bbf27-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="bbf27-117">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="bbf27-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="bbf27-118">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bbf27-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="bbf27-119">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="bbf27-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="bbf27-120">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bbf27-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="bbf27-121">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="bbf27-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="bbf27-122">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bbf27-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf27-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbf27-123">See also</span></span>

- [<span data-ttu-id="bbf27-124">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="bbf27-124">Unmanaged API Reference</span></span>](../index.md)
