---
title: Método StrongNameSignatureVerificationEx2
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d2ac3788b68626eb04a6f2cbac995b8e5b4ebf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442576"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="028dc-102">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="028dc-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="028dc-103">Verifica a assinatura de um assembly de nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="028dc-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="028dc-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="028dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="028dc-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="028dc-106">[in] O caminho para o executável (.exe ou. dll) arquivo portátil para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="028dc-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="028dc-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="028dc-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="028dc-108">[in] Um ponteiro para o mapeamento da chave pública ECMA para a chave usada para verificação.</span><span class="sxs-lookup"><span data-stu-id="028dc-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="028dc-109">[in] O comprimento da chave pública ECMA real.</span><span class="sxs-lookup"><span data-stu-id="028dc-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="028dc-110">[out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="028dc-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="028dc-111">Esse parâmetro também é definido como `false` se a verificação for bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="028dc-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="028dc-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="028dc-112">Return Value</span></span>  
 <span data-ttu-id="028dc-113">`S_OK` Se a verificação for bem-sucedida; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="028dc-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028dc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="028dc-114">Requirements</span></span>  
 <span data-ttu-id="028dc-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="028dc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="028dc-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="028dc-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="028dc-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="028dc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="028dc-118">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="028dc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028dc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="028dc-119">See Also</span></span>  
 [<span data-ttu-id="028dc-120">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="028dc-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="028dc-121">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="028dc-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="028dc-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="028dc-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
