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
ms.openlocfilehash: d3693a42db8e32a4bb7a399f8c930da011130893
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778730"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="0cdde-102">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="0cdde-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="0cdde-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="0cdde-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="0cdde-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="0cdde-104">This function has been deprecated.</span></span> <span data-ttu-id="0cdde-105">Use o [iclrstrongname:: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0cdde-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cdde-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cdde-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cdde-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cdde-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="0cdde-108">[in] O caminho para o assembly primeiro.</span><span class="sxs-lookup"><span data-stu-id="0cdde-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="0cdde-109">[in] O caminho para o segundo conjunto.</span><span class="sxs-lookup"><span data-stu-id="0cdde-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="0cdde-110">[out] Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0cdde-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="0cdde-111">`SN_CMP_DIFFERENT` (0) – Especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="0cdde-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="0cdde-112">`SN_CMP_IDENTICAL` (1) - Especifica que os assemblies são exatamente os mesmos, incluindo suas assinaturas e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="0cdde-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="0cdde-113">`SN_CMP_SIGONLY` (2) - Especifica que os assemblies diferem somente por assinatura e a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="0cdde-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cdde-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0cdde-114">Return Value</span></span>  
 <span data-ttu-id="0cdde-115">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0cdde-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cdde-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0cdde-116">Requirements</span></span>  
 <span data-ttu-id="0cdde-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cdde-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cdde-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0cdde-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0cdde-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0cdde-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0cdde-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cdde-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cdde-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cdde-121">Remarks</span></span>  
 <span data-ttu-id="0cdde-122">A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="0cdde-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="0cdde-123">Se o `StrongNameCompareAssemblies` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="0cdde-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdde-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cdde-124">See also</span></span>

- [<span data-ttu-id="0cdde-125">Método StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="0cdde-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="0cdde-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0cdde-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
