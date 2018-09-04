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
ms.openlocfilehash: e47c2ac69317b2d2db489dce9a0102b5fe304c05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556592"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="28a6a-102">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="28a6a-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="28a6a-103">Verifica a assinatura de um assembly de nome forte e fornece um mapeamento da chave do ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="28a6a-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28a6a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28a6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28a6a-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="28a6a-106">[in] O caminho para o arquivo executável portátil (.exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="28a6a-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="28a6a-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="28a6a-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="28a6a-108">[in] Um ponteiro para o mapeamento da chave pública do ECMA para a chave real usado para verificação.</span><span class="sxs-lookup"><span data-stu-id="28a6a-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="28a6a-109">[in] O comprimento da chave pública real do ECMA.</span><span class="sxs-lookup"><span data-stu-id="28a6a-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="28a6a-110">[out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="28a6a-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="28a6a-111">Esse parâmetro também é definido como `false` se a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="28a6a-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28a6a-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="28a6a-112">Return Value</span></span>  
 <span data-ttu-id="28a6a-113">`S_OK` Se a verificação for bem-sucedida; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="28a6a-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28a6a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28a6a-114">Requirements</span></span>  
 <span data-ttu-id="28a6a-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28a6a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28a6a-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="28a6a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="28a6a-117">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="28a6a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28a6a-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28a6a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a6a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28a6a-119">See Also</span></span>  
 [<span data-ttu-id="28a6a-120">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="28a6a-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="28a6a-121">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="28a6a-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="28a6a-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="28a6a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
