---
title: Função StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191374"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="03b02-102">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="03b02-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="03b02-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="03b02-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="03b02-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="03b02-104">This function has been deprecated.</span></span> <span data-ttu-id="03b02-105">Use o [iclrstrongname:: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="03b02-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b02-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03b02-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03b02-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03b02-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="03b02-108">[in] O caminho para o assembly primeiro.</span><span class="sxs-lookup"><span data-stu-id="03b02-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="03b02-109">[in] O caminho para o segundo conjunto.</span><span class="sxs-lookup"><span data-stu-id="03b02-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="03b02-110">[out] Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="03b02-110">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="03b02-111">(0) – Especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="03b02-111">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="03b02-112">(1) - Especifica que os assemblies são exatamente os mesmos, incluindo suas assinaturas e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="03b02-112">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="03b02-113">(2) - Especifica que os assemblies diferem somente por assinatura e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="03b02-113">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03b02-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="03b02-114">Return Value</span></span>  
 `true` <span data-ttu-id="03b02-115">Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="03b02-115">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03b02-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03b02-116">Requirements</span></span>  
 <span data-ttu-id="03b02-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03b02-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03b02-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="03b02-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="03b02-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="03b02-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="03b02-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="03b02-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="03b02-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="03b02-121">Remarks</span></span>  
 <span data-ttu-id="03b02-122">A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="03b02-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="03b02-123">Se o `StrongNameCompareAssemblies` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="03b02-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b02-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03b02-124">See also</span></span>

- [<span data-ttu-id="03b02-125">Método StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="03b02-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="03b02-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="03b02-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
