---
title: Estrutura SYMLINEDELTA
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77cd8b7d791d11f6d40386f4747c60cd4832521a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="30f4a-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="30f4a-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="30f4a-103">Fornece informações sobre os métodos que foram movidos em decorrência de edições para o manipulador de símbolo.</span><span class="sxs-lookup"><span data-stu-id="30f4a-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30f4a-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="30f4a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="30f4a-105">Members</span></span>  
  
|<span data-ttu-id="30f4a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="30f4a-106">Member</span></span>|<span data-ttu-id="30f4a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30f4a-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="30f4a-108">Token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="30f4a-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="30f4a-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="30f4a-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30f4a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30f4a-110">Requirements</span></span>  
 <span data-ttu-id="30f4a-111">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="30f4a-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f4a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30f4a-112">See Also</span></span>  
 [<span data-ttu-id="30f4a-113">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="30f4a-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
