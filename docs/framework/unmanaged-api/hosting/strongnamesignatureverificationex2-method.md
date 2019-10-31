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
ms.openlocfilehash: cf8d6b7e45c0012d223173c85a92fac4fb044c6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141404"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="e19cf-102">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="e19cf-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="e19cf-103">Verifica a assinatura de um assembly com nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="e19cf-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e19cf-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e19cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e19cf-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e19cf-106">no O caminho para o arquivo executável portátil (. exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="e19cf-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="e19cf-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e19cf-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="e19cf-108">no Um ponteiro para o mapeamento da chave pública ECMA para a chave real usada para verificação.</span><span class="sxs-lookup"><span data-stu-id="e19cf-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="e19cf-109">no O comprimento da chave pública ECMA real.</span><span class="sxs-lookup"><span data-stu-id="e19cf-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="e19cf-110">[fora] `true` se a assinatura de nome forte foi verificada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e19cf-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="e19cf-111">Esse parâmetro também é definido como `false` se a verificação foi bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="e19cf-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e19cf-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e19cf-112">Return Value</span></span>  
 <span data-ttu-id="e19cf-113">`S_OK` se a verificação foi bem-sucedida; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="e19cf-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e19cf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e19cf-114">Requirements</span></span>  
 <span data-ttu-id="e19cf-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e19cf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e19cf-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e19cf-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e19cf-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e19cf-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e19cf-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e19cf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19cf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e19cf-119">See also</span></span>

- [<span data-ttu-id="e19cf-120">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="e19cf-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="e19cf-121">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="e19cf-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="e19cf-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e19cf-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
