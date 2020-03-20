---
title: Função StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176910"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="72b9a-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="72b9a-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="72b9a-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="72b9a-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="72b9a-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="72b9a-104">This function has been deprecated.</span></span> <span data-ttu-id="72b9a-105">Use o método [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72b9a-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b9a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72b9a-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b9a-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="72b9a-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="72b9a-108">[em] Um ponteiro para a memória para libertar.</span><span class="sxs-lookup"><span data-stu-id="72b9a-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72b9a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72b9a-109">Requirements</span></span>  
 <span data-ttu-id="72b9a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72b9a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b9a-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="72b9a-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72b9a-112">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72b9a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72b9a-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b9a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b9a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="72b9a-114">See also</span></span>

- [<span data-ttu-id="72b9a-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="72b9a-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="72b9a-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="72b9a-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
