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
ms.openlocfilehash: 2d534ae381e0dc105731cf0a537f81afe80d87e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732733"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="922bb-102">Estrutura SYMLINEDELTA</span><span class="sxs-lookup"><span data-stu-id="922bb-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="922bb-103">Fornece informações para o manipulador de símbolo sobre os métodos que foram movidos em decorrência de edições.</span><span class="sxs-lookup"><span data-stu-id="922bb-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="922bb-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="922bb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="922bb-105">Members</span></span>  
  
|<span data-ttu-id="922bb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="922bb-106">Member</span></span>|<span data-ttu-id="922bb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="922bb-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="922bb-108">Token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="922bb-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="922bb-109">O número de linhas que o método foi movido.</span><span class="sxs-lookup"><span data-stu-id="922bb-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="922bb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="922bb-110">Requirements</span></span>  
 <span data-ttu-id="922bb-111">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="922bb-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="922bb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="922bb-112">See also</span></span>
- [<span data-ttu-id="922bb-113">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="922bb-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
