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
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140627"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="efa99-102">Função StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="efa99-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="efa99-103">Determina se dois assemblies diferem somente por suas assinaturas de nome forte.</span><span class="sxs-lookup"><span data-stu-id="efa99-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="efa99-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="efa99-104">This function has been deprecated.</span></span> <span data-ttu-id="efa99-105">Em vez disso, use o método [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .</span><span class="sxs-lookup"><span data-stu-id="efa99-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efa99-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efa99-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efa99-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efa99-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="efa99-108">no O caminho para o primeiro assembly.</span><span class="sxs-lookup"><span data-stu-id="efa99-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="efa99-109">no O caminho para o segundo assembly.</span><span class="sxs-lookup"><span data-stu-id="efa99-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="efa99-110">fora Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="efa99-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="efa99-111">`SN_CMP_DIFFERENT` (0) – especifica que os assemblies contêm dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="efa99-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="efa99-112">`SN_CMP_IDENTICAL` (1) – especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="efa99-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="efa99-113">`SN_CMP_SIGONLY` (2) – especifica que os assemblies diferem somente por assinatura e soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="efa99-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efa99-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="efa99-114">Return Value</span></span>  
 <span data-ttu-id="efa99-115">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="efa99-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efa99-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efa99-116">Requirements</span></span>  
 <span data-ttu-id="efa99-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efa99-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efa99-118">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="efa99-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="efa99-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efa99-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efa99-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efa99-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efa99-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="efa99-121">Remarks</span></span>  
 <span data-ttu-id="efa99-122">A assinatura de nome forte de um assembly consiste no nome de texto, versão, cultura e token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="efa99-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="efa99-123">Se a função `StrongNameCompareAssemblies` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="efa99-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa99-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efa99-124">See also</span></span>

- [<span data-ttu-id="efa99-125">Método StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="efa99-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="efa99-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="efa99-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
