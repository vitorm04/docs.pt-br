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
ms.openlocfilehash: d98ebed2eb853d5dc8177b0b044bf654c3978494
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744353"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="8c88b-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="8c88b-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="8c88b-103">Fornece informações para o manipulador de símbolo sobre os métodos que foram movidos em decorrência de edições.</span><span class="sxs-lookup"><span data-stu-id="8c88b-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c88b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c88b-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="8c88b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8c88b-105">Members</span></span>  
  
|<span data-ttu-id="8c88b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8c88b-106">Member</span></span>|<span data-ttu-id="8c88b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c88b-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="8c88b-108">Token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="8c88b-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="8c88b-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="8c88b-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c88b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c88b-110">Requirements</span></span>  
 <span data-ttu-id="8c88b-111">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="8c88b-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c88b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c88b-112">See also</span></span>

- [<span data-ttu-id="8c88b-113">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="8c88b-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
