---
title: Método ICLRStrongName::StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d4b885b6968b800bc965a9be1ec6b795a42220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140654"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="7fdf4-102">Método ICLRStrongName::StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="7fdf4-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="7fdf4-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdf4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fdf4-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fdf4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdf4-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="7fdf4-106">[in] O caminho para o assembly primeiro.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="7fdf4-107">[in] O caminho para o segundo conjunto.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="7fdf4-108">[out] Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7fdf4-108">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="7fdf4-109">(0) – Especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-109">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="7fdf4-110">(1) - Especifica que os assemblies são exatamente os mesmos, incluindo suas assinaturas e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-110">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="7fdf4-111">(2) - Especifica que os assemblies diferem somente por assinatura e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-111">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fdf4-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7fdf4-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="7fdf4-113">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="7fdf4-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fdf4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fdf4-114">Requirements</span></span>  
 <span data-ttu-id="7fdf4-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fdf4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fdf4-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7fdf4-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7fdf4-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7fdf4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7fdf4-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7fdf4-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="7fdf4-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fdf4-119">Remarks</span></span>  
 <span data-ttu-id="7fdf4-120">A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="7fdf4-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fdf4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fdf4-121">See also</span></span>

- [<span data-ttu-id="7fdf4-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7fdf4-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
