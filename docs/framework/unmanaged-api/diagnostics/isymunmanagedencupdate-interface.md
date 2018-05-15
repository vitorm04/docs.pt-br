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
ms.openlocfilehash: 05cbe098b73dd817546dd72f0fc98ad548f75386
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="d295e-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="d295e-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="d295e-103">Fornece funções para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="d295e-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d295e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d295e-104">Methods</span></span>  
  
|<span data-ttu-id="d295e-105">Método</span><span class="sxs-lookup"><span data-stu-id="d295e-105">Method</span></span>|<span data-ttu-id="d295e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d295e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d295e-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="d295e-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="d295e-108">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="d295e-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="d295e-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="d295e-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="d295e-110">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="d295e-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="d295e-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="d295e-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="d295e-112">Permite que os limites de método deve ser calculada antes da primeira chamada para o [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="d295e-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="d295e-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="d295e-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="d295e-114">Permite atualizar as informações de linha para um método que não foi recompilado, mas cujas linhas foram movidos independentemente.</span><span class="sxs-lookup"><span data-stu-id="d295e-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d295e-115">Um delta para cada instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="d295e-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="d295e-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="d295e-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="d295e-117">Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="d295e-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="d295e-118">As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="d295e-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d295e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d295e-119">Requirements</span></span>  
 <span data-ttu-id="d295e-120">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d295e-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d295e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d295e-121">See Also</span></span>  
 [<span data-ttu-id="d295e-122">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d295e-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
