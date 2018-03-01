---
title: Interface ISymUnmanagedENCUpdate
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f68d000824779fcffb90ec031b86b50e8c80eccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="f9135-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="f9135-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="f9135-103">Fornece funções para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="f9135-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9135-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f9135-104">Methods</span></span>  
  
|<span data-ttu-id="f9135-105">Método</span><span class="sxs-lookup"><span data-stu-id="f9135-105">Method</span></span>|<span data-ttu-id="f9135-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9135-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9135-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="f9135-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="f9135-108">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f9135-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="f9135-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="f9135-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="f9135-110">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f9135-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="f9135-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="f9135-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="f9135-112">Permite que os limites de método deve ser calculada antes da primeira chamada para o [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f9135-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="f9135-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="f9135-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="f9135-114">Permite atualizar as informações de linha para um método que não foi recompilado, mas cujas linhas foram movidos independentemente.</span><span class="sxs-lookup"><span data-stu-id="f9135-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="f9135-115">Um delta para cada instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="f9135-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="f9135-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="f9135-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="f9135-117">Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="f9135-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="f9135-118">As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="f9135-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9135-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9135-119">Requirements</span></span>  
 <span data-ttu-id="f9135-120">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9135-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9135-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9135-121">See Also</span></span>  
 [<span data-ttu-id="f9135-122">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="f9135-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
