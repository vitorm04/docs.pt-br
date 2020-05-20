---
title: Método ISymUnmanagedWriter2::DefineGlobalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: ed3c841c34b71b30f740117899353aa289e478d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614702"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="06fa5-102">Método ISymUnmanagedWriter2::DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="06fa5-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="06fa5-103">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="06fa5-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fa5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06fa5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06fa5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06fa5-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="06fa5-106">no O nome da variável global.</span><span class="sxs-lookup"><span data-stu-id="06fa5-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="06fa5-107">no Os atributos da variável global.</span><span class="sxs-lookup"><span data-stu-id="06fa5-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="06fa5-108">no O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="06fa5-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="06fa5-109">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="06fa5-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="06fa5-110">no O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06fa5-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="06fa5-111">no O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06fa5-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="06fa5-112">no O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06fa5-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06fa5-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="06fa5-113">Return Value</span></span>  
 <span data-ttu-id="06fa5-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="06fa5-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fa5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06fa5-115">Requirements</span></span>  
 <span data-ttu-id="06fa5-116">**Cabeçalho:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="06fa5-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fa5-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="06fa5-117">See also</span></span>

- [<span data-ttu-id="06fa5-118">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="06fa5-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="06fa5-119">Método DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="06fa5-119">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
