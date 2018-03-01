---
title: "Função CertVerifyAuthenticodeLicense"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bab3a3bcee52a302345ccdcfad81e7f67efdd8d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="346dc-102">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="346dc-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="346dc-103">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="346dc-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="346dc-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="346dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="346dc-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="346dc-106">[In] A licença XrML Authenticode a ser verificada.</span><span class="sxs-lookup"><span data-stu-id="346dc-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="346dc-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="346dc-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="346dc-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="346dc-108">[in] Optional.</span></span> <span data-ttu-id="346dc-109">Uma combinação dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="346dc-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="346dc-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="346dc-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="346dc-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="346dc-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="346dc-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="346dc-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="346dc-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="346dc-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="346dc-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="346dc-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="346dc-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="346dc-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="346dc-116">[out] Para receber informações do assinante.</span><span class="sxs-lookup"><span data-stu-id="346dc-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="346dc-117">Se a licença não foi assinada, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="346dc-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="346dc-118">É responsabilidade do chamador para liberar recursos usando o [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) função após o uso.</span><span class="sxs-lookup"><span data-stu-id="346dc-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="346dc-119">Consulte [estrutura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="346dc-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="346dc-120">[out] Para receber informações do carimbo de hora, se disponível.</span><span class="sxs-lookup"><span data-stu-id="346dc-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="346dc-121">Se a licença não recebeu carimbo de hora, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="346dc-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="346dc-122">É responsabilidade do chamador para liberar recursos usando o [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) função após o uso.</span><span class="sxs-lookup"><span data-stu-id="346dc-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="346dc-123">Consulte [estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="346dc-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="346dc-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="346dc-124">Return Value</span></span>  
 <span data-ttu-id="346dc-125">Retorna `S_OK` se houver êxito.</span><span class="sxs-lookup"><span data-stu-id="346dc-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="346dc-126">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="346dc-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346dc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="346dc-127">See Also</span></span>  
 [<span data-ttu-id="346dc-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="346dc-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [<span data-ttu-id="346dc-129">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="346dc-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="346dc-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="346dc-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
