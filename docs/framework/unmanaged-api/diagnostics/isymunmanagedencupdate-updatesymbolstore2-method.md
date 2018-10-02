---
title: Método ISymUnmanagedENCUpdate::UpdateSymbolStore2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78d9e27299c9d7ed7d6cb9b09dd659ba081c5fde
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030779"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="e4ade-102">Método ISymUnmanagedENCUpdate::UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="e4ade-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="e4ade-103">Permite que um compilador omitir as funções que não foram modificadas desde o fluxo do programa (PDB) do banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="e4ade-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="e4ade-104">As informações de linha corretas podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="e4ade-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ade-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4ade-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4ade-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4ade-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="e4ade-107">[in] Um ponteiro para um [IStream](/windows/desktop/api/objidl/nn-objidl-istream) que contém as informações de linha.</span><span class="sxs-lookup"><span data-stu-id="e4ade-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="e4ade-108">[in] Um ponteiro para um [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) estrutura que contém as linhas que foram alterados.</span><span class="sxs-lookup"><span data-stu-id="e4ade-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="e4ade-109">[in] Um `ULONG` que representa o número de linhas que foram alterados.</span><span class="sxs-lookup"><span data-stu-id="e4ade-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4ade-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e4ade-110">Return Value</span></span>  
 <span data-ttu-id="e4ade-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e4ade-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ade-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4ade-112">Requirements</span></span>  
 <span data-ttu-id="e4ade-113">**Cabeçalho:** Corsym, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4ade-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ade-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4ade-114">See Also</span></span>  
 [<span data-ttu-id="e4ade-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="e4ade-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
