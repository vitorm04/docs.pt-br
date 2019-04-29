---
title: Função StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049b7b11473a05d74dc311ca6ee79947039b0dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794401"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="c2908-102">Função StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="c2908-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="c2908-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="c2908-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="c2908-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c2908-104">This function has been deprecated.</span></span> <span data-ttu-id="c2908-105">Use o [iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c2908-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2908-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2908-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2908-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2908-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c2908-108">[in] O caminho para o arquivo executável portátil (.exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="c2908-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="c2908-109">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c2908-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="c2908-110">[out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c2908-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="c2908-111">`pfWasVerified` também é definido como `false` se a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="c2908-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2908-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c2908-112">Return Value</span></span>  
 <span data-ttu-id="c2908-113">`true` Se a verificação for bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c2908-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2908-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2908-114">Remarks</span></span>  
 <span data-ttu-id="c2908-115">`StrongNameSignatureVerificationEx` Fornece uma funcionalidade semelhante para o [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="c2908-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="c2908-116">No entanto, o segundo parâmetro de entrada e o parâmetro de saída para `StrongNameSignatureVerificationEx` são do tipo `BOOLEAN` em vez de `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="c2908-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2908-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2908-117">Requirements</span></span>  
 <span data-ttu-id="c2908-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2908-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2908-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c2908-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c2908-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c2908-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="c2908-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2908-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2908-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2908-122">See also</span></span>

- [<span data-ttu-id="c2908-123">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="c2908-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="c2908-124">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="c2908-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="c2908-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c2908-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
