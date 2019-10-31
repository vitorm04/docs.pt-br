---
title: Função StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121139"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="bf425-102">Função StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="bf425-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="bf425-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="bf425-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="bf425-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="bf425-104">This function has been deprecated.</span></span> <span data-ttu-id="bf425-105">Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf425-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf425-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf425-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf425-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf425-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="bf425-108">no O caminho para o arquivo executável portátil (. exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="bf425-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="bf425-109">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bf425-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="bf425-110">[fora] `true` se a assinatura de nome forte foi verificada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bf425-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="bf425-111">`pfWasVerified` também será definido como `false` se a verificação tiver sido bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="bf425-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf425-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bf425-112">Return Value</span></span>  
 <span data-ttu-id="bf425-113">`true` se a verificação foi bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bf425-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf425-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf425-114">Remarks</span></span>  
 <span data-ttu-id="bf425-115">`StrongNameSignatureVerificationEx` fornece um recurso semelhante à função [StrongNameSignatureVerification](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bf425-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="bf425-116">No entanto, o segundo parâmetro de entrada e o parâmetro de saída para `StrongNameSignatureVerificationEx` são do tipo `BOOLEAN` em vez de `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bf425-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf425-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf425-117">Requirements</span></span>  
 <span data-ttu-id="bf425-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf425-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf425-119">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bf425-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bf425-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bf425-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="bf425-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf425-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf425-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf425-122">See also</span></span>

- [<span data-ttu-id="bf425-123">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="bf425-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="bf425-124">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="bf425-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="bf425-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bf425-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
