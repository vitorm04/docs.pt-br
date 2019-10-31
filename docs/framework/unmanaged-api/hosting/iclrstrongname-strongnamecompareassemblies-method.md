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
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135157"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="c3dec-102">Método ICLRStrongName::StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="c3dec-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="c3dec-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="c3dec-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3dec-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3dec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3dec-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="c3dec-106">no O caminho para o primeiro assembly.</span><span class="sxs-lookup"><span data-stu-id="c3dec-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="c3dec-107">no O caminho para o segundo assembly.</span><span class="sxs-lookup"><span data-stu-id="c3dec-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="c3dec-108">fora Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c3dec-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="c3dec-109">`SN_CMP_DIFFERENT` (0) – especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="c3dec-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="c3dec-110">`SN_CMP_IDENTICAL` (1) – especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="c3dec-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="c3dec-111">`SN_CMP_SIGONLY` (2) – especifica que os assemblies diferem somente por assinatura e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="c3dec-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3dec-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c3dec-112">Return Value</span></span>  
 <span data-ttu-id="c3dec-113">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="c3dec-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3dec-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3dec-114">Requirements</span></span>  
 <span data-ttu-id="c3dec-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3dec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dec-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c3dec-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c3dec-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3dec-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3dec-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3dec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3dec-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3dec-119">Remarks</span></span>  
 <span data-ttu-id="c3dec-120">A assinatura de nome forte de um assembly consiste no nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="c3dec-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dec-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3dec-121">See also</span></span>

- [<span data-ttu-id="c3dec-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c3dec-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
