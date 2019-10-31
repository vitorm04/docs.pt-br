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
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095057"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="3a734-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="3a734-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="3a734-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="3a734-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="3a734-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="3a734-104">This function has been deprecated.</span></span> <span data-ttu-id="3a734-105">Em vez disso, use o método [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a734-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a734-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a734-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a734-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a734-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="3a734-108">no Um ponteiro para a memória para liberar.</span><span class="sxs-lookup"><span data-stu-id="3a734-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a734-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a734-109">Requirements</span></span>  
 <span data-ttu-id="3a734-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a734-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a734-111">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3a734-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3a734-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a734-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a734-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a734-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a734-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a734-114">See also</span></span>

- [<span data-ttu-id="3a734-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="3a734-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="3a734-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3a734-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
