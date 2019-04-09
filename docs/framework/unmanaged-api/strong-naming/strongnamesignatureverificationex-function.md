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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112899"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="feea8-102">Função StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="feea8-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="feea8-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="feea8-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="feea8-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="feea8-104">This function has been deprecated.</span></span> <span data-ttu-id="feea8-105">Use o [iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="feea8-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feea8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="feea8-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feea8-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="feea8-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="feea8-108">[in] O caminho para o arquivo executável portátil (.exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="feea8-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="feea8-109">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="feea8-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="feea8-110">[out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="feea8-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> `pfWasVerified` <span data-ttu-id="feea8-111">também é definido como `false` se a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="feea8-111">is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feea8-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="feea8-112">Return Value</span></span>  
 `true` <span data-ttu-id="feea8-113">Se a verificação for bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="feea8-113">if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feea8-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="feea8-114">Remarks</span></span>  
 `StrongNameSignatureVerificationEx` <span data-ttu-id="feea8-115">Fornece uma funcionalidade semelhante para o [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="feea8-115">provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="feea8-116">No entanto, o segundo parâmetro de entrada e o parâmetro de saída para `StrongNameSignatureVerificationEx` são do tipo `BOOLEAN` em vez de `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="feea8-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feea8-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="feea8-117">Requirements</span></span>  
 <span data-ttu-id="feea8-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feea8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feea8-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="feea8-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="feea8-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="feea8-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="feea8-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="feea8-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="feea8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feea8-122">See also</span></span>

- [<span data-ttu-id="feea8-123">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="feea8-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="feea8-124">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="feea8-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="feea8-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="feea8-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
