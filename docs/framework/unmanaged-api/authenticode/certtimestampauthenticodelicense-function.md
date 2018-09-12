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
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508537"
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="e1143-102">Função CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="e1143-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="e1143-103">Carimbo de data/hora em uma licença Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="e1143-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1143-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1143-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1143-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1143-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="e1143-106">[in] A licença Authenticode XrML assinada a receber o carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="e1143-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="e1143-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="e1143-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="e1143-108">[in] O URI do servidor de carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="e1143-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="e1143-109">[out] Um ponteiro para CRYPT_DATA_BLOB para receber a assinatura do carimbo de data/hora codificado por base64.</span><span class="sxs-lookup"><span data-stu-id="e1143-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="e1143-110">É responsabilidade do chamador liberar `pTimestampSignatureBlob` -> `pbData` com `HepFree()` após o uso.</span><span class="sxs-lookup"><span data-stu-id="e1143-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="e1143-111">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="e1143-111">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1143-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1143-112">Remarks</span></span>  
 <span data-ttu-id="e1143-113">A assinatura do carimbo de data/hora é, na realidade, uma mensagem PKCS #7 SignedData cujo conteúdo é o formulário binário do SignatureValue da assinatura da licença.</span><span class="sxs-lookup"><span data-stu-id="e1143-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="e1143-114">Basicamente, isso funciona como uma referenda da licença.</span><span class="sxs-lookup"><span data-stu-id="e1143-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1143-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e1143-115">Return Value</span></span>  
 <span data-ttu-id="e1143-116">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e1143-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e1143-117">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e1143-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1143-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1143-118">See Also</span></span>  
 [<span data-ttu-id="e1143-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e1143-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
