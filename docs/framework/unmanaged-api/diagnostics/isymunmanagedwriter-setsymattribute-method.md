---
title: Método ISymUnmanagedWriter::SetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 39b0c065a324f2b3939467901739f995bc9abbad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614754"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="3071c-102">Método ISymUnmanagedWriter::SetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="3071c-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="3071c-103">Define um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="3071c-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="3071c-104">Esses atributos são mantidos no repositório de símbolos, ao contrário dos atributos personalizados de metadados.</span><span class="sxs-lookup"><span data-stu-id="3071c-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3071c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3071c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3071c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3071c-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3071c-107">no O token de metadados para o qual o atributo está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="3071c-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="3071c-108">no Um ponteiro para um `WCHAR` que contém o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="3071c-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="3071c-109">no Um `ULONG32` que indica o tamanho da `data` matriz.</span><span class="sxs-lookup"><span data-stu-id="3071c-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="3071c-110">no O valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="3071c-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3071c-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3071c-111">Return Value</span></span>  
 <span data-ttu-id="3071c-112">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3071c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3071c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3071c-113">Requirements</span></span>  
 <span data-ttu-id="3071c-114">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3071c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3071c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3071c-115">See also</span></span>

- [<span data-ttu-id="3071c-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="3071c-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
