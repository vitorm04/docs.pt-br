---
title: Método ISymUnmanagedWriter::DefineParameter
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: c695aa80ea3bf90a29ce7c5d11eda7fae5fe7b2d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614806"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="e6431-102">Método ISymUnmanagedWriter::DefineParameter</span><span class="sxs-lookup"><span data-stu-id="e6431-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="e6431-103">Define um único parâmetro no método atual.</span><span class="sxs-lookup"><span data-stu-id="e6431-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="e6431-104">O tipo de parâmetro é obtido da posição do parâmetro (sequência) na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="e6431-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="e6431-105">Se os parâmetros forem definidos nos metadados de um determinado método, você não precisará defini-los novamente usando esse método.</span><span class="sxs-lookup"><span data-stu-id="e6431-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="e6431-106">Os leitores de símbolo devem verificar os metadados normais dos parâmetros antes de verificar o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e6431-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6431-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6431-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6431-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6431-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e6431-109">no O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="e6431-110">no Os atributos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="e6431-111">no A assinatura do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="e6431-112">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="e6431-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="e6431-113">no O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="e6431-114">no O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="e6431-115">no O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e6431-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6431-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e6431-116">Return Value</span></span>  
 <span data-ttu-id="e6431-117">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e6431-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6431-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6431-118">Requirements</span></span>  
 <span data-ttu-id="e6431-119">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e6431-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6431-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6431-120">See also</span></span>

- [<span data-ttu-id="e6431-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="e6431-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
