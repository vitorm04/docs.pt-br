---
title: "Função StrongNameCompareAssemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3453cffb5e98e3623565785ab64db4f455be981
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="6ebd4-102">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="6ebd4-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="6ebd4-103">Determina se os dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="6ebd4-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-104">This function has been deprecated.</span></span> <span data-ttu-id="6ebd4-105">Use o [: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebd4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ebd4-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ebd4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ebd4-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="6ebd4-108">[in] O caminho para o primeiro conjunto.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="6ebd4-109">[in] O caminho para o segundo conjunto.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="6ebd4-110">[out] Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6ebd4-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="6ebd4-111">`SN_CMP_DIFFERENT`(0) - Especifica que os assemblies conterem dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="6ebd4-112">`SN_CMP_IDENTICAL`(1) - Especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="6ebd4-113">`SN_CMP_SIGONLY`(2) - Especifica que os assemblies diferem somente por assinatura e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ebd4-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6ebd4-114">Return Value</span></span>  
 <span data-ttu-id="6ebd4-115">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ebd4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ebd4-116">Requirements</span></span>  
 <span data-ttu-id="6ebd4-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebd4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebd4-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6ebd4-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6ebd4-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6ebd4-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ebd4-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ebd4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ebd4-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ebd4-121">Remarks</span></span>  
 <span data-ttu-id="6ebd4-122">A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="6ebd4-123">Se o `StrongNameCompareAssemblies` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="6ebd4-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebd4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ebd4-124">See Also</span></span>  
 [<span data-ttu-id="6ebd4-125">Método StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="6ebd4-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [<span data-ttu-id="6ebd4-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6ebd4-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
