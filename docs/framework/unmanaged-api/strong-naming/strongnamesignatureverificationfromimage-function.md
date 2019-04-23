---
title: Função StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54b1d35d1c40289bad465978750ba738acf28c90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212434"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="53f85-102">Função StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="53f85-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="53f85-103">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="53f85-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="53f85-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="53f85-104">This function has been deprecated.</span></span> <span data-ttu-id="53f85-105">Use o [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="53f85-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f85-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53f85-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53f85-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53f85-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="53f85-108">[in] O endereço virtual relativo do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="53f85-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="53f85-109">[in] O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="53f85-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="53f85-110">[in] Sinalizadores que influenciam o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="53f85-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="53f85-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="53f85-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="53f85-112">`SN_INFLAG_FORCE_VER` (0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="53f85-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="53f85-113">`SN_INFLAG_INSTALL` (0x00000002) - Especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="53f85-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="53f85-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="53f85-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="53f85-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="53f85-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="53f85-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="53f85-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="53f85-117">`SN_INFLAG_RUNTIME` (0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="53f85-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="53f85-118">[out] Um sinalizador para obter informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="53f85-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="53f85-119">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="53f85-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="53f85-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="53f85-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53f85-121">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="53f85-121">Return Value</span></span>  
 <span data-ttu-id="53f85-122">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="53f85-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53f85-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="53f85-123">Remarks</span></span>  
 <span data-ttu-id="53f85-124">Se o `StrongNameSignatureVerificationFromImage` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="53f85-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53f85-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53f85-125">Requirements</span></span>  
 <span data-ttu-id="53f85-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53f85-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f85-127">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="53f85-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="53f85-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="53f85-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="53f85-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f85-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f85-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53f85-130">See also</span></span>

- [<span data-ttu-id="53f85-131">Método StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="53f85-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="53f85-132">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="53f85-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
