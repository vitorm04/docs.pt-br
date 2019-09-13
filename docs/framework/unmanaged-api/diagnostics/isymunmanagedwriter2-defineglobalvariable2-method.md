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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a54d3cb1bb9abf740c2c9b5a9a8312a9612ae658
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894459"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="fa97b-102">Método ISymUnmanagedWriter2::DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="fa97b-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="fa97b-103">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="fa97b-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa97b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa97b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fa97b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa97b-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fa97b-106">no O nome da variável global.</span><span class="sxs-lookup"><span data-stu-id="fa97b-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="fa97b-107">no Os atributos da variável global.</span><span class="sxs-lookup"><span data-stu-id="fa97b-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="fa97b-108">no O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="fa97b-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="fa97b-109">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="fa97b-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="fa97b-110">no O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa97b-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="fa97b-111">no O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa97b-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="fa97b-112">no O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fa97b-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa97b-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fa97b-113">Return Value</span></span>  
 <span data-ttu-id="fa97b-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fa97b-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa97b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa97b-115">Requirements</span></span>  
 <span data-ttu-id="fa97b-116">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="fa97b-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa97b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa97b-117">See also</span></span>

- [<span data-ttu-id="fa97b-118">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="fa97b-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="fa97b-119">Método DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="fa97b-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
