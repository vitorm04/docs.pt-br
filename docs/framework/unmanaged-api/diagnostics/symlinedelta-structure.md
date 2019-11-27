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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438004"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="df9b8-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="df9b8-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="df9b8-103">Fornece informações para o manipulador de símbolos sobre métodos que foram movidos como resultado de edições.</span><span class="sxs-lookup"><span data-stu-id="df9b8-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df9b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df9b8-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="df9b8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="df9b8-105">Members</span></span>  
  
|<span data-ttu-id="df9b8-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="df9b8-106">Member</span></span>|<span data-ttu-id="df9b8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="df9b8-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="df9b8-108">O token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="df9b8-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="df9b8-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="df9b8-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df9b8-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="df9b8-110">Requirements</span></span>  
 <span data-ttu-id="df9b8-111">**Cabeçalho:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="df9b8-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9b8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df9b8-112">See also</span></span>

- [<span data-ttu-id="df9b8-113">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="df9b8-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
