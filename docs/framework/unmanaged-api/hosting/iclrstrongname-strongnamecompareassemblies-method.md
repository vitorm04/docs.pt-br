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
ms.openlocfilehash: 0087636c68d0748ad2b143de9b132278ab9d43f5
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762052"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="11409-102">Método ICLRStrongName::StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="11409-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="11409-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="11409-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11409-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11409-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11409-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11409-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="11409-106">no O caminho para o primeiro assembly.</span><span class="sxs-lookup"><span data-stu-id="11409-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="11409-107">no O caminho para o segundo assembly.</span><span class="sxs-lookup"><span data-stu-id="11409-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="11409-108">fora Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="11409-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="11409-109">`SN_CMP_DIFFERENT`(0)-especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="11409-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="11409-110">`SN_CMP_IDENTICAL`(1)-especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="11409-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="11409-111">`SN_CMP_SIGONLY`(2)-especifica que os assemblies diferem somente por assinatura e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="11409-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11409-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="11409-112">Return Value</span></span>  
 <span data-ttu-id="11409-113">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="11409-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11409-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11409-114">Requirements</span></span>  
 <span data-ttu-id="11409-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11409-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11409-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="11409-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="11409-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11409-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11409-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11409-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11409-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="11409-119">Remarks</span></span>  
 <span data-ttu-id="11409-120">A assinatura de nome forte de um assembly consiste no nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="11409-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11409-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="11409-121">See also</span></span>

- [<span data-ttu-id="11409-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="11409-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
