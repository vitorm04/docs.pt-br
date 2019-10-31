---
title: Função StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: 5c12ca20deee06fcaca68365644fd9dff95379ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121153"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="e5c27-102">Função StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="e5c27-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="e5c27-103">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="e5c27-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="e5c27-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="e5c27-104">This function has been deprecated.</span></span> <span data-ttu-id="e5c27-105">Em vez disso, use o método [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e5c27-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c27-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5c27-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5c27-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5c27-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="e5c27-108">no O endereço virtual relativo do manifesto do assembly mapeado.</span><span class="sxs-lookup"><span data-stu-id="e5c27-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e5c27-109">no O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="e5c27-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e5c27-110">no Sinalizadores que influenciam o comportamento da verificação.</span><span class="sxs-lookup"><span data-stu-id="e5c27-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="e5c27-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="e5c27-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="e5c27-112">`SN_INFLAG_FORCE_VER` (0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="e5c27-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="e5c27-113">`SN_INFLAG_INSTALL` (0x00000002) – especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="e5c27-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="e5c27-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="e5c27-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="e5c27-115">`SN_INFLAG_USER_ACCESS` (0x00000008) – especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="e5c27-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="e5c27-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) – especifica que o cache não fornecerá nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="e5c27-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="e5c27-117">`SN_INFLAG_RUNTIME` (0x80000000) – reservado para depuração interna.</span><span class="sxs-lookup"><span data-stu-id="e5c27-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e5c27-118">fora Um sinalizador para informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="e5c27-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="e5c27-119">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="e5c27-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="e5c27-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="e5c27-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5c27-121">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e5c27-121">Return Value</span></span>  
 <span data-ttu-id="e5c27-122">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e5c27-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c27-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5c27-123">Remarks</span></span>  
 <span data-ttu-id="e5c27-124">Se a função `StrongNameSignatureVerificationFromImage` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="e5c27-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c27-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5c27-125">Requirements</span></span>  
 <span data-ttu-id="e5c27-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c27-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c27-127">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="e5c27-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e5c27-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e5c27-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="e5c27-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c27-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c27-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5c27-130">See also</span></span>

- [<span data-ttu-id="e5c27-131">Método StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="e5c27-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="e5c27-132">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e5c27-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
