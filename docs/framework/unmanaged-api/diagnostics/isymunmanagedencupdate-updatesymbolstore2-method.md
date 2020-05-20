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
ms.openlocfilehash: f363bed8e7002bf898755b434c919f8722dea3fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614494"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="bd07b-102">Método ISymUnmanagedENCUpdate::UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="bd07b-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="bd07b-103">Permite que um compilador omita funções que não foram modificadas do fluxo do banco de dados do programa (PDB), desde que as informações da linha atendam aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="bd07b-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="bd07b-104">As informações de linha corretas podem ser determinadas com as informações da linha PDB antiga e um Delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="bd07b-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd07b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd07b-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd07b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd07b-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="bd07b-107">no Um ponteiro para um [IStream](/windows/desktop/api/objidl/nn-objidl-istream) que contém as informações de linha.</span><span class="sxs-lookup"><span data-stu-id="bd07b-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="bd07b-108">no Um ponteiro para uma estrutura [SYMLINEDELTA](symlinedelta-structure.md) que contém as linhas que foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="bd07b-108">[in] A pointer to a [SYMLINEDELTA](symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="bd07b-109">no Um `ULONG` que representa o número de linhas que foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="bd07b-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd07b-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bd07b-110">Return Value</span></span>  
 <span data-ttu-id="bd07b-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bd07b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd07b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd07b-112">Requirements</span></span>  
 <span data-ttu-id="bd07b-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bd07b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd07b-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="bd07b-114">See also</span></span>

- [<span data-ttu-id="bd07b-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="bd07b-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
