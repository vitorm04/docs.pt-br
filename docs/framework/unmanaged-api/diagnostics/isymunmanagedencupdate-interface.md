---
title: Interface ISymUnmanagedENCUpdate
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="729d7-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="729d7-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="729d7-103">Fornece funções para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="729d7-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="729d7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="729d7-104">Methods</span></span>  
  
|<span data-ttu-id="729d7-105">Método</span><span class="sxs-lookup"><span data-stu-id="729d7-105">Method</span></span>|<span data-ttu-id="729d7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="729d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="729d7-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="729d7-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="729d7-108">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="729d7-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="729d7-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="729d7-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="729d7-110">Obtém as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="729d7-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="729d7-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="729d7-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="729d7-112">Permite que os limites de método deve ser calculada antes da primeira chamada para o [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="729d7-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="729d7-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="729d7-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="729d7-114">Permite atualizar as informações de linha para um método que não foi recompilado, mas cujas linhas foram movidos independentemente.</span><span class="sxs-lookup"><span data-stu-id="729d7-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="729d7-115">Um delta para cada instrução é permitida.</span><span class="sxs-lookup"><span data-stu-id="729d7-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="729d7-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="729d7-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="729d7-117">Permite que um compilador para omitir as funções que não foram modificadas desde o fluxo do programa (PDB) de banco de dados, desde que as informações de linha atende aos requisitos.</span><span class="sxs-lookup"><span data-stu-id="729d7-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="729d7-118">As informações corretas de linha podem ser determinadas com as informações de linha PDB antigas e um delta para todas as linhas na função.</span><span class="sxs-lookup"><span data-stu-id="729d7-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="729d7-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="729d7-119">Requirements</span></span>  
 <span data-ttu-id="729d7-120">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="729d7-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729d7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="729d7-121">See Also</span></span>  
 [<span data-ttu-id="729d7-122">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="729d7-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
