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
ms.openlocfilehash: 02eaaa1c3336b6e99b8c8deabb944e292e35a2a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425164"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="e4a23-102">Método ISymUnmanagedENCUpdate::UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="e4a23-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="e4a23-103">Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="e4a23-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="e4a23-104">As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="e4a23-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a23-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4a23-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4a23-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4a23-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="e4a23-107">[in] Um ponteiro para um [IStream](https://msdn.microsoft.com/library/aa380034.aspx) que contém as informações de linha.</span><span class="sxs-lookup"><span data-stu-id="e4a23-107">[in] A pointer to an [IStream](https://msdn.microsoft.com/library/aa380034.aspx) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="e4a23-108">[in] Um ponteiro para um [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) estrutura que contém as linhas que foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="e4a23-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="e4a23-109">[in] Um `ULONG` que representa o número de linhas que foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="e4a23-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4a23-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e4a23-110">Return Value</span></span>  
 <span data-ttu-id="e4a23-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e4a23-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a23-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4a23-112">Requirements</span></span>  
 <span data-ttu-id="e4a23-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4a23-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a23-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4a23-114">See Also</span></span>  
 [<span data-ttu-id="e4a23-115">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="e4a23-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
