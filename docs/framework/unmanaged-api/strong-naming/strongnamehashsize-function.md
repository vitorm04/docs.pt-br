---
title: Função StrongNameHashSize
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: c656f73748faf8be7124be65f3ed455f2d5fd07a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105188"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="b5722-102">Função StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="b5722-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="b5722-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="b5722-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="b5722-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="b5722-104">This function has been deprecated.</span></span> <span data-ttu-id="b5722-105">Em vez disso, use o método [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b5722-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5722-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5722-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5722-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5722-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="b5722-108">no O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="b5722-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="b5722-109">fora O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b5722-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5722-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b5722-110">Return Value</span></span>  
 <span data-ttu-id="b5722-111">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b5722-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5722-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5722-112">Remarks</span></span>  
 <span data-ttu-id="b5722-113">Se a função `StrongNameHashSize` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="b5722-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5722-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5722-114">Requirements</span></span>  
 <span data-ttu-id="b5722-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5722-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5722-116">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b5722-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b5722-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b5722-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5722-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5722-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5722-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5722-119">See also</span></span>

- [<span data-ttu-id="b5722-120">Método StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="b5722-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="b5722-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b5722-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
