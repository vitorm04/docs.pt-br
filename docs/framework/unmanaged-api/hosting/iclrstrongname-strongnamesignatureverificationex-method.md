---
title: "Método ICLRStrongName::StrongNameSignatureVerificationEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerificationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f44d644f95395d1dde22536bd2855e335d65f358
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="dafdd-102">Método ICLRStrongName::StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="dafdd-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="dafdd-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="dafdd-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dafdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dafdd-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dafdd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dafdd-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dafdd-106">[in] O caminho para o executável (.exe ou. dll) arquivo portátil para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="dafdd-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="dafdd-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="dafdd-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="dafdd-108">[out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="dafdd-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="dafdd-109">`pfWasVerified`também é definido como `false` se a verificação for bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="dafdd-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dafdd-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dafdd-110">Return Value</span></span>  
 <span data-ttu-id="dafdd-111">`S_OK`Se a verificação for bem-sucedida; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="dafdd-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dafdd-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="dafdd-112">Remarks</span></span>  
 <span data-ttu-id="dafdd-113">O [: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) método fornece uma funcionalidade semelhante para o [Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="dafdd-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="dafdd-114">No entanto, o segundo parâmetro de entrada e o parâmetro de saída para [: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) são do tipo `BOOLEAN` em vez de `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="dafdd-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dafdd-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dafdd-115">Requirements</span></span>  
 <span data-ttu-id="dafdd-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dafdd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dafdd-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dafdd-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dafdd-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dafdd-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dafdd-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dafdd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dafdd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dafdd-120">See Also</span></span>  
 [<span data-ttu-id="dafdd-121">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="dafdd-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="dafdd-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="dafdd-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
