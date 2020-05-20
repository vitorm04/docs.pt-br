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
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609294"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="94ad5-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="94ad5-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="94ad5-103">Fornece informações para o manipulador de símbolos sobre métodos que foram movidos como resultado de edições.</span><span class="sxs-lookup"><span data-stu-id="94ad5-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ad5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94ad5-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="94ad5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="94ad5-105">Members</span></span>  
  
|<span data-ttu-id="94ad5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="94ad5-106">Member</span></span>|<span data-ttu-id="94ad5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ad5-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="94ad5-108">O token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="94ad5-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="94ad5-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="94ad5-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94ad5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94ad5-110">Requirements</span></span>  
 <span data-ttu-id="94ad5-111">**Cabeçalho:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="94ad5-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ad5-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="94ad5-112">See also</span></span>

- [<span data-ttu-id="94ad5-113">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="94ad5-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
