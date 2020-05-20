---
title: Método ISymUnmanagedReader2::GetSymAttributePreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: e6248aba1c41b2815f2806942d419da869ed94b4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614910"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="82e5f-102">Método ISymUnmanagedReader2::GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="82e5f-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="82e5f-103">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="82e5f-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="82e5f-104">Ao contrário dos atributos personalizados de metadados, esses atributos são mantidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="82e5f-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e5f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82e5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e5f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82e5f-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="82e5f-107">no O token de metadados do pai.</span><span class="sxs-lookup"><span data-stu-id="82e5f-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="82e5f-108">no Um ponteiro para um `WCHAR` que contém o nome.</span><span class="sxs-lookup"><span data-stu-id="82e5f-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="82e5f-109">no Um `ULONG32` que indica o tamanho da `buffer` matriz.</span><span class="sxs-lookup"><span data-stu-id="82e5f-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="82e5f-110">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os bytes do atributo.</span><span class="sxs-lookup"><span data-stu-id="82e5f-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="82e5f-111">fora Um ponteiro para o buffer que recebe os bytes de atributo.</span><span class="sxs-lookup"><span data-stu-id="82e5f-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e5f-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="82e5f-112">Return Value</span></span>  
 <span data-ttu-id="82e5f-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="82e5f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e5f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82e5f-114">Requirements</span></span>  
 <span data-ttu-id="82e5f-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="82e5f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e5f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="82e5f-116">See also</span></span>

- [<span data-ttu-id="82e5f-117">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="82e5f-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
