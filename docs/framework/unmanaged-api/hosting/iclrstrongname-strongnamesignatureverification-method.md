---
title: Método ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9fb7098c29768821cafad6662b646eb0e08a138
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212837"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="ca93b-102">Método ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="ca93b-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="ca93b-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="ca93b-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca93b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca93b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca93b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca93b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ca93b-106">[in] O caminho para o arquivo executável portátil (. dll ou .exe) para o assembly verificar.</span><span class="sxs-lookup"><span data-stu-id="ca93b-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="ca93b-107">[in] Sinalizadores para modificar o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="ca93b-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="ca93b-108">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ca93b-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ca93b-109">`SN_INFLAG_FORCE_VER` (0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="ca93b-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="ca93b-110">`SN_INFLAG_INSTALL` (0x00000002) - Especifica que esta é a primeira vez que o manifesto é verificado.</span><span class="sxs-lookup"><span data-stu-id="ca93b-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="ca93b-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="ca93b-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="ca93b-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="ca93b-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="ca93b-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="ca93b-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="ca93b-114">`SN_INFLAG_RUNTIME` (0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="ca93b-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="ca93b-115">[out] Sinalizadores que indica se a assinatura de nome forte foi verificada.</span><span class="sxs-lookup"><span data-stu-id="ca93b-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="ca93b-116">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="ca93b-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="ca93b-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="ca93b-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca93b-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca93b-118">Return Value</span></span>  
 <span data-ttu-id="ca93b-119">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="ca93b-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca93b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca93b-120">Requirements</span></span>  
 <span data-ttu-id="ca93b-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca93b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca93b-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ca93b-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ca93b-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ca93b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca93b-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca93b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca93b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca93b-125">See also</span></span>

- [<span data-ttu-id="ca93b-126">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="ca93b-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="ca93b-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ca93b-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
