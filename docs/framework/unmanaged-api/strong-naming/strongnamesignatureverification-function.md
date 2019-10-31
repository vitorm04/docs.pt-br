---
title: Função StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129239"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="42bbf-102">Função StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="42bbf-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="42bbf-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="42bbf-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="42bbf-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="42bbf-104">This function has been deprecated.</span></span> <span data-ttu-id="42bbf-105">Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42bbf-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42bbf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42bbf-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42bbf-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42bbf-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="42bbf-108">no O caminho para o arquivo executável portátil (. dll ou. exe) para o assembly verificar.</span><span class="sxs-lookup"><span data-stu-id="42bbf-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="42bbf-109">no Sinalizadores para modificar o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="42bbf-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="42bbf-110">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="42bbf-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="42bbf-111">`SN_INFLAG_FORCE_VER` (0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="42bbf-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="42bbf-112">`SN_INFLAG_INSTALL` (0x00000002) – especifica que esta é a primeira vez que o manifesto é verificado.</span><span class="sxs-lookup"><span data-stu-id="42bbf-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="42bbf-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="42bbf-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="42bbf-114">`SN_INFLAG_USER_ACCESS` (0x00000008) – especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="42bbf-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="42bbf-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) – especifica que o cache não fornecerá nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="42bbf-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="42bbf-116">`SN_INFLAG_RUNTIME` (0x80000000) – reservado para depuração interna.</span><span class="sxs-lookup"><span data-stu-id="42bbf-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="42bbf-117">fora Sinalizadores que indicam se a assinatura de nome forte foi verificada.</span><span class="sxs-lookup"><span data-stu-id="42bbf-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="42bbf-118">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="42bbf-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="42bbf-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="42bbf-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42bbf-120">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="42bbf-120">Return Value</span></span>  
 <span data-ttu-id="42bbf-121">`true` se a verificação foi bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="42bbf-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42bbf-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42bbf-122">Requirements</span></span>  
 <span data-ttu-id="42bbf-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42bbf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42bbf-124">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="42bbf-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="42bbf-125">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="42bbf-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42bbf-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42bbf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bbf-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42bbf-127">See also</span></span>

- [<span data-ttu-id="42bbf-128">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="42bbf-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="42bbf-129">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="42bbf-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="42bbf-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="42bbf-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
