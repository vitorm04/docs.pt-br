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
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="467bf-102">Função CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="467bf-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="467bf-103">Verifica a validade de uma licença XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="467bf-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="467bf-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="467bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="467bf-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="467bf-106">[In] A licença XrML Authenticode a ser verificada.</span><span class="sxs-lookup"><span data-stu-id="467bf-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="467bf-107">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="467bf-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="467bf-108">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="467bf-108">[in] Optional.</span></span> <span data-ttu-id="467bf-109">Uma combinação dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="467bf-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="467bf-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="467bf-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="467bf-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="467bf-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="467bf-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="467bf-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="467bf-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="467bf-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="467bf-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="467bf-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="467bf-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="467bf-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="467bf-116">[out] Para receber informações do assinante.</span><span class="sxs-lookup"><span data-stu-id="467bf-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="467bf-117">Se a licença não foi assinada, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="467bf-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="467bf-118">É responsabilidade do chamador liberar recursos usando a função [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) após o uso.</span><span class="sxs-lookup"><span data-stu-id="467bf-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="467bf-119">Consulte [estrutura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="467bf-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="467bf-120">[out] Para receber informações do carimbo de hora, se disponível.</span><span class="sxs-lookup"><span data-stu-id="467bf-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="467bf-121">Se a licença não recebeu carimbo de hora, `dwError` é definido como TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="467bf-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="467bf-122">É responsabilidade do chamador liberar recursos usando a função [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) após o uso.</span><span class="sxs-lookup"><span data-stu-id="467bf-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="467bf-123">Consulte [estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="467bf-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="467bf-124">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="467bf-124">Return Value</span></span>  
 <span data-ttu-id="467bf-125">Retorna `S_OK` se houver êxito.</span><span class="sxs-lookup"><span data-stu-id="467bf-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="467bf-126">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="467bf-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467bf-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="467bf-127">See also</span></span>

- [<span data-ttu-id="467bf-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="467bf-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="467bf-129">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="467bf-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="467bf-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="467bf-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
