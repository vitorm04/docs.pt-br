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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06f69bf867b565edbab06dadb32e5377357e91f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617693"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="3ea59-102">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="3ea59-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="3ea59-103">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="3ea59-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ea59-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea59-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ea59-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="3ea59-106">[In] A licença XrML Authenticode a ser verificada.</span><span class="sxs-lookup"><span data-stu-id="3ea59-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="3ea59-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="3ea59-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3ea59-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="3ea59-108">[in] Optional.</span></span> <span data-ttu-id="3ea59-109">Uma combinação dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="3ea59-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="3ea59-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="3ea59-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="3ea59-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="3ea59-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="3ea59-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="3ea59-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="3ea59-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="3ea59-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="3ea59-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="3ea59-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="3ea59-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="3ea59-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="3ea59-116">[out] Para receber informações do assinante.</span><span class="sxs-lookup"><span data-stu-id="3ea59-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="3ea59-117">Se a licença não foi assinada, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="3ea59-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="3ea59-118">É responsabilidade do chamador liberar recursos por meio de [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) função após o uso.</span><span class="sxs-lookup"><span data-stu-id="3ea59-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="3ea59-119">Ver [estrutura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="3ea59-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="3ea59-120">[out] Para receber informações do carimbo de hora, se disponível.</span><span class="sxs-lookup"><span data-stu-id="3ea59-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="3ea59-121">Se a licença não recebeu carimbo de hora, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="3ea59-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="3ea59-122">É responsabilidade do chamador liberar recursos por meio de [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) função após o uso.</span><span class="sxs-lookup"><span data-stu-id="3ea59-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="3ea59-123">Ver [estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="3ea59-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea59-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3ea59-124">Return Value</span></span>  
 <span data-ttu-id="3ea59-125">Retorna `S_OK` se houver êxito.</span><span class="sxs-lookup"><span data-stu-id="3ea59-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="3ea59-126">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="3ea59-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea59-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ea59-127">See also</span></span>

- [<span data-ttu-id="3ea59-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3ea59-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [<span data-ttu-id="3ea59-129">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="3ea59-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="3ea59-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3ea59-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
