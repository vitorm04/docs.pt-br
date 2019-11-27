---
title: Interface ISymUnmanagedENCUpdate
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449009"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="4f145-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="4f145-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="4f145-103">Fornece funções para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="4f145-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f145-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4f145-104">Methods</span></span>  
  
|<span data-ttu-id="4f145-105">Método</span><span class="sxs-lookup"><span data-stu-id="4f145-105">Method</span></span>|<span data-ttu-id="4f145-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f145-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f145-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="4f145-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="4f145-108">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="4f145-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="4f145-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="4f145-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="4f145-110">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="4f145-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="4f145-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="4f145-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="4f145-112">Permite que os limites de método sejam computados antes da primeira chamada para o método [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f145-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="4f145-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="4f145-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="4f145-114">Permite atualizar as informações de linha de um método que não foi recompilado, mas cujas linhas foram movidas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="4f145-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="4f145-115">Um Delta para cada instrução é permitido.</span><span class="sxs-lookup"><span data-stu-id="4f145-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="4f145-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="4f145-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="4f145-117">Permite que um compilador omita funções que não foram modificadas do fluxo do banco de dados do programa (PDB), desde que as informações da linha atendam aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="4f145-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="4f145-118">As informações de linha corretas podem ser determinadas com as informações da linha PDB antiga e um Delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="4f145-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f145-119">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4f145-119">Requirements</span></span>  
 <span data-ttu-id="4f145-120">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4f145-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f145-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f145-121">See also</span></span>

- [<span data-ttu-id="4f145-122">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4f145-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
