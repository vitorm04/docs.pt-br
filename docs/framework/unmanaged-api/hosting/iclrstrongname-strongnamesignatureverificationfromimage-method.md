---
title: Método ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e09ac96a8803f41d78b532c9da67315e5dd6b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113731"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="5e137-102">Método ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="5e137-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="5e137-103">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="5e137-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e137-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e137-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e137-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e137-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="5e137-106">[in] O endereço virtual relativo do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="5e137-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5e137-107">[in] O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="5e137-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="5e137-108">[in] Sinalizadores que influenciam o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="5e137-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="5e137-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="5e137-109">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="5e137-110">(0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="5e137-110">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="5e137-111">(0x00000002) - Especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="5e137-111">(0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="5e137-112">(0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="5e137-112">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="5e137-113">(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5e137-113">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="5e137-114">(0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="5e137-114">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="5e137-115">(0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="5e137-115">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="5e137-116">[out] Um sinalizador para obter informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="5e137-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="5e137-117">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="5e137-117">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="5e137-118">(0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="5e137-118">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e137-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5e137-119">Return Value</span></span>  
 `S_OK` <span data-ttu-id="5e137-120">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="5e137-120">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e137-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e137-121">Requirements</span></span>  
 <span data-ttu-id="5e137-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e137-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e137-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5e137-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e137-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5e137-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5e137-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5e137-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e137-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e137-126">See also</span></span>

- [<span data-ttu-id="5e137-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="5e137-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
