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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 378322c28d59b2a6e7c09f2f2c4bf55bb019d01d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171828"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="811c1-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="811c1-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="811c1-103">Fornece funções para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="811c1-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="811c1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="811c1-104">Methods</span></span>  
  
|<span data-ttu-id="811c1-105">Método</span><span class="sxs-lookup"><span data-stu-id="811c1-105">Method</span></span>|<span data-ttu-id="811c1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="811c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="811c1-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="811c1-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="811c1-108">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="811c1-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="811c1-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="811c1-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="811c1-110">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="811c1-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="811c1-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="811c1-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="811c1-112">Permite que os limites de método a ser computado antes da primeira chamada para o [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="811c1-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="811c1-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="811c1-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="811c1-114">Permite atualizar as informações de linha para um método que não foram recompilado, mas cujas linhas foram movidas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="811c1-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="811c1-115">Um delta para cada instrução é permitido.</span><span class="sxs-lookup"><span data-stu-id="811c1-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="811c1-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="811c1-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="811c1-117">Permite que um compilador omitir as funções que não foram modificadas desde o fluxo do programa (PDB) do banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="811c1-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="811c1-118">As informações de linha corretas podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="811c1-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="811c1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="811c1-119">Requirements</span></span>  
 <span data-ttu-id="811c1-120">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="811c1-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811c1-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="811c1-121">See also</span></span>

- [<span data-ttu-id="811c1-122">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="811c1-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
