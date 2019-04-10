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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212434"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="3f8fb-102">Função StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="3f8fb-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="3f8fb-103">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="3f8fb-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-104">This function has been deprecated.</span></span> <span data-ttu-id="3f8fb-105">Use o [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8fb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f8fb-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f8fb-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f8fb-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="3f8fb-108">[in] O endereço virtual relativo do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3f8fb-109">[in] O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="3f8fb-110">[in] Sinalizadores que influenciam o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="3f8fb-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="3f8fb-111">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="3f8fb-112">(0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-112">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="3f8fb-113">(0x00000002) - Especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-113">(0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="3f8fb-114">(0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-114">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="3f8fb-115">(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-115">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="3f8fb-116">(0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-116">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="3f8fb-117">(0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-117">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="3f8fb-118">[out] Um sinalizador para obter informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="3f8fb-119">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="3f8fb-119">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="3f8fb-120">(0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-120">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f8fb-121">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3f8fb-121">Return Value</span></span>  
 `true` <span data-ttu-id="3f8fb-122">Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-122">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f8fb-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f8fb-123">Remarks</span></span>  
 <span data-ttu-id="3f8fb-124">Se o `StrongNameSignatureVerificationFromImage` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="3f8fb-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f8fb-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f8fb-125">Requirements</span></span>  
 <span data-ttu-id="3f8fb-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f8fb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f8fb-127">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3f8fb-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3f8fb-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3f8fb-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="3f8fb-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3f8fb-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f8fb-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f8fb-130">See also</span></span>

- [<span data-ttu-id="3f8fb-131">Método StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="3f8fb-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="3f8fb-132">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3f8fb-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
