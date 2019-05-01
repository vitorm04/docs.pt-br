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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000318"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="a939c-102">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="a939c-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="a939c-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="a939c-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="a939c-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="a939c-104">This function has been deprecated.</span></span> <span data-ttu-id="a939c-105">Use o [iclrstrongname:: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a939c-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a939c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a939c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a939c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a939c-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="a939c-108">[in] O caminho para o assembly primeiro.</span><span class="sxs-lookup"><span data-stu-id="a939c-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="a939c-109">[in] O caminho para o segundo conjunto.</span><span class="sxs-lookup"><span data-stu-id="a939c-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="a939c-110">[out] Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a939c-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="a939c-111">`SN_CMP_DIFFERENT` (0) – Especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="a939c-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="a939c-112">`SN_CMP_IDENTICAL` (1) - Especifica que os assemblies são exatamente os mesmos, incluindo suas assinaturas e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="a939c-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="a939c-113">`SN_CMP_SIGONLY` (2) - Especifica que os assemblies diferem somente por assinatura e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="a939c-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a939c-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a939c-114">Return Value</span></span>  
 <span data-ttu-id="a939c-115">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a939c-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a939c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a939c-116">Requirements</span></span>  
 <span data-ttu-id="a939c-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a939c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a939c-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a939c-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a939c-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a939c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a939c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a939c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a939c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="a939c-121">Remarks</span></span>  
 <span data-ttu-id="a939c-122">A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="a939c-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="a939c-123">Se o `StrongNameCompareAssemblies` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="a939c-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a939c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a939c-124">See also</span></span>

- [<span data-ttu-id="a939c-125">Método StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="a939c-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="a939c-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a939c-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
