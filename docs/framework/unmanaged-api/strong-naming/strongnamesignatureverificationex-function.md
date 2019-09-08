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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798919"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="2d18d-102">Função StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="2d18d-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="2d18d-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="2d18d-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="2d18d-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="2d18d-104">This function has been deprecated.</span></span> <span data-ttu-id="2d18d-105">Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2d18d-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d18d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d18d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d18d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d18d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2d18d-108">no O caminho para o arquivo executável portátil (. exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="2d18d-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="2d18d-109">no para executar a verificação, mesmo que seja necessário substituir as configurações do registro; caso `false`contrário,. `true`</span><span class="sxs-lookup"><span data-stu-id="2d18d-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="2d18d-110">fora se a assinatura de nome forte foi verificada; caso contrário, `false`. `true`</span><span class="sxs-lookup"><span data-stu-id="2d18d-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="2d18d-111">`pfWasVerified`também será definido como `false` se a verificação tiver sido bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="2d18d-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d18d-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2d18d-112">Return Value</span></span>  
 <span data-ttu-id="2d18d-113">`true`se a verificação foi bem-sucedida; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="2d18d-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d18d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d18d-114">Remarks</span></span>  
 <span data-ttu-id="2d18d-115">`StrongNameSignatureVerificationEx`fornece um recurso semelhante à função [StrongNameSignatureVerification](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="2d18d-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="2d18d-116">No entanto, o segundo parâmetro de entrada e o `StrongNameSignatureVerificationEx` parâmetro de saída `BOOLEAN` para são `DWORD`do tipo em vez de.</span><span class="sxs-lookup"><span data-stu-id="2d18d-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d18d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d18d-117">Requirements</span></span>  
 <span data-ttu-id="2d18d-118">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d18d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d18d-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2d18d-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2d18d-120">**Biblioteca** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2d18d-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="2d18d-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d18d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d18d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d18d-122">See also</span></span>

- [<span data-ttu-id="2d18d-123">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="2d18d-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="2d18d-124">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="2d18d-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="2d18d-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2d18d-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
