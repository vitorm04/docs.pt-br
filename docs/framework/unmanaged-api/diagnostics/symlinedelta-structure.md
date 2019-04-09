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
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159478"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="bb749-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="bb749-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="bb749-103">Fornece informações para o manipulador de símbolo sobre os métodos que foram movidos em decorrência de edições.</span><span class="sxs-lookup"><span data-stu-id="bb749-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb749-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb749-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="bb749-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bb749-105">Members</span></span>  
  
|<span data-ttu-id="bb749-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bb749-106">Member</span></span>|<span data-ttu-id="bb749-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb749-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="bb749-108">Token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="bb749-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="bb749-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="bb749-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb749-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb749-110">Requirements</span></span>  
 <span data-ttu-id="bb749-111">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="bb749-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb749-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb749-112">See also</span></span>

- [<span data-ttu-id="bb749-113">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bb749-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
