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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799032"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="c28e5-102">Função StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="c28e5-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="c28e5-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="c28e5-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c28e5-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c28e5-104">This function has been deprecated.</span></span> <span data-ttu-id="c28e5-105">Em vez disso, use o método [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c28e5-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28e5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c28e5-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c28e5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c28e5-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="c28e5-108">no O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="c28e5-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c28e5-109">fora O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c28e5-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c28e5-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c28e5-110">Return Value</span></span>  
 <span data-ttu-id="c28e5-111">`true`após a conclusão bem-sucedida; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="c28e5-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c28e5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c28e5-112">Remarks</span></span>  
 <span data-ttu-id="c28e5-113">Se a `StrongNameHashSize` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="c28e5-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28e5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c28e5-114">Requirements</span></span>  
 <span data-ttu-id="c28e5-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28e5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28e5-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c28e5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c28e5-117">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c28e5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c28e5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28e5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c28e5-119">See also</span></span>

- [<span data-ttu-id="c28e5-120">Método StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="c28e5-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="c28e5-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c28e5-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
