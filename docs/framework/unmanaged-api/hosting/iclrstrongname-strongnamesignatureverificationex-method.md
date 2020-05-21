---
title: Método ICLRStrongName::StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: e2003ce78f04b101fe093867e0820f9c3840151a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762702"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="9a56d-102">Método ICLRStrongName::StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="9a56d-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="9a56d-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9a56d-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a56d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a56d-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a56d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a56d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9a56d-106">no O caminho para o arquivo executável portátil (. exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="9a56d-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="9a56d-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="9a56d-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="9a56d-108">[fora] `true` se a assinatura de nome forte foi verificada; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="9a56d-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="9a56d-109">`pfWasVerified`também será definido como `false` se a verificação tiver sido bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="9a56d-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a56d-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9a56d-110">Return Value</span></span>  
 <span data-ttu-id="9a56d-111">`S_OK`se a verificação foi bem-sucedida; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="9a56d-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a56d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a56d-112">Remarks</span></span>  
 <span data-ttu-id="9a56d-113">O método [ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) fornece um recurso semelhante ao método [ICLRStrongName:: StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a56d-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="9a56d-114">No entanto, o segundo parâmetro de entrada e o parâmetro de saída para [ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) são do tipo `BOOLEAN` em vez de `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="9a56d-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a56d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a56d-115">Requirements</span></span>  
 <span data-ttu-id="9a56d-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a56d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a56d-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9a56d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9a56d-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a56d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a56d-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a56d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a56d-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="9a56d-120">See also</span></span>

- [<span data-ttu-id="9a56d-121">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="9a56d-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="9a56d-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9a56d-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
