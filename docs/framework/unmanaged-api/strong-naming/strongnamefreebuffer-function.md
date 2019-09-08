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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 639664c6ce5714b554f30bff2569a12bf48d1671
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799129"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="05bd4-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="05bd4-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="05bd4-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="05bd4-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="05bd4-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="05bd4-104">This function has been deprecated.</span></span> <span data-ttu-id="05bd4-105">Em vez disso, use o método [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="05bd4-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bd4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05bd4-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05bd4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05bd4-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="05bd4-108">no Um ponteiro para a memória para liberar.</span><span class="sxs-lookup"><span data-stu-id="05bd4-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05bd4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05bd4-109">Requirements</span></span>  
 <span data-ttu-id="05bd4-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05bd4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05bd4-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="05bd4-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="05bd4-112">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05bd4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05bd4-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05bd4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bd4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05bd4-114">See also</span></span>

- [<span data-ttu-id="05bd4-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="05bd4-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="05bd4-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="05bd4-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
