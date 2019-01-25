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
ms.openlocfilehash: a6e4b323f9e06f2c5dc336af772bdade0db3dea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657435"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="69e9f-102">Método ISymUnmanagedWriter2::DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="69e9f-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="69e9f-103">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="69e9f-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69e9f-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69e9f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69e9f-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="69e9f-106">[in] O nome da variável global.</span><span class="sxs-lookup"><span data-stu-id="69e9f-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="69e9f-107">[in] Atributos da variável global.</span><span class="sxs-lookup"><span data-stu-id="69e9f-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="69e9f-108">[in] O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="69e9f-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="69e9f-109">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="69e9f-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="69e9f-110">[in] O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69e9f-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="69e9f-111">[in] O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69e9f-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="69e9f-112">[in] O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69e9f-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69e9f-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="69e9f-113">Return Value</span></span>  
 <span data-ttu-id="69e9f-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="69e9f-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e9f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69e9f-115">Requirements</span></span>  
 <span data-ttu-id="69e9f-116">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="69e9f-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e9f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69e9f-117">See also</span></span>
- [<span data-ttu-id="69e9f-118">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="69e9f-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="69e9f-119">Método DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="69e9f-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
