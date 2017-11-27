---
title: "Função CertTimestampAuthenticodeLicense"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="75f8c-102">Função CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="75f8c-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="75f8c-103">Carimbo de data/hora em uma licença Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="75f8c-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75f8c-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75f8c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75f8c-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="75f8c-106">[in] A licença Authenticode XrML assinada a receber o carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="75f8c-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="75f8c-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="75f8c-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="75f8c-108">[in] O URI do servidor de carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="75f8c-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="75f8c-109">[out] Um ponteiro para CRYPT_DATA_BLOB para receber a assinatura do carimbo de data/hora codificado por base64.</span><span class="sxs-lookup"><span data-stu-id="75f8c-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="75f8c-110">É responsabilidade do chamador para liberar `pTimestampSignatureBlob` -> `pbData` com `HepFree()` após o uso.</span><span class="sxs-lookup"><span data-stu-id="75f8c-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="75f8c-111">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="75f8c-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f8c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="75f8c-112">Remarks</span></span>  
 <span data-ttu-id="75f8c-113">A assinatura do carimbo de data/hora é, na realidade, uma mensagem PKCS #7 SignedData cujo conteúdo é o formulário binário do SignatureValue da assinatura da licença.</span><span class="sxs-lookup"><span data-stu-id="75f8c-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="75f8c-114">Basicamente, isso funciona como uma referenda da licença.</span><span class="sxs-lookup"><span data-stu-id="75f8c-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75f8c-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="75f8c-115">Return Value</span></span>  
 <span data-ttu-id="75f8c-116">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="75f8c-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="75f8c-117">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="75f8c-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f8c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75f8c-118">See Also</span></span>  
 [<span data-ttu-id="75f8c-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="75f8c-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
