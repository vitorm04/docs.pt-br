---
title: Método ISymUnmanagedWriter::DefineField
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: aba551a1973a41a909869316cda07e8d655e9882
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614832"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="eb96d-102">Método ISymUnmanagedWriter::DefineField</span><span class="sxs-lookup"><span data-stu-id="eb96d-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="eb96d-103">Define uma única variável que não está dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="eb96d-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="eb96d-104">Esse método é usado para determinados campos em classes, campos de bits e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="eb96d-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb96d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb96d-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb96d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb96d-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="eb96d-107">no O tipo de metadados ou o token do método.</span><span class="sxs-lookup"><span data-stu-id="eb96d-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="eb96d-108">no O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="eb96d-109">no Os atributos do campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="eb96d-110">no Um `ULONG32` que é o tamanho, em caracteres, do buffer necessário para conter a assinatura de campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="eb96d-111">no A matriz de assinaturas de campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="eb96d-112">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="eb96d-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="eb96d-113">no O primeiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="eb96d-114">no O segundo endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="eb96d-115">no O terceiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="eb96d-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb96d-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="eb96d-116">Return Value</span></span>  
 <span data-ttu-id="eb96d-117">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="eb96d-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb96d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb96d-118">Requirements</span></span>  
 <span data-ttu-id="eb96d-119">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eb96d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb96d-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb96d-120">See also</span></span>

- [<span data-ttu-id="eb96d-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="eb96d-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
