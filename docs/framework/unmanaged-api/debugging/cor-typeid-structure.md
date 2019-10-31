---
title: Estrutura COR_TYPEID
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132303"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="fa749-102">Estrutura COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="fa749-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="fa749-103">Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="fa749-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa749-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa749-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="fa749-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fa749-105">Members</span></span>  
  
|<span data-ttu-id="fa749-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fa749-106">Member</span></span>|<span data-ttu-id="fa749-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa749-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="fa749-108">O primeiro token.</span><span class="sxs-lookup"><span data-stu-id="fa749-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="fa749-109">O segundo token.</span><span class="sxs-lookup"><span data-stu-id="fa749-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa749-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa749-110">Remarks</span></span>  
 <span data-ttu-id="fa749-111">A estrutura de `COR_TYPEID` é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="fa749-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="fa749-112">Em seguida, ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item.</span><span class="sxs-lookup"><span data-stu-id="fa749-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="fa749-113">Por exemplo, enumerando um objeto [ICorDebugHeapEnum](icordebugheapenum-interface.md) , você pode recuperar objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) individuais que representam objetos individuais no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fa749-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="fa749-114">Em seguida, você pode passar o valor `COR_TYPEID` do campo `COR_HEAPOBJECT.type` para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) para recuperar um objeto ICorDebugType que fornece informações de tipo sobre o objeto.</span><span class="sxs-lookup"><span data-stu-id="fa749-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="fa749-115">Um objeto `COR_TYPEID` destina-se a ser opaco.</span><span class="sxs-lookup"><span data-stu-id="fa749-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="fa749-116">Seus campos individuais não devem ser acessados ou manipulados.</span><span class="sxs-lookup"><span data-stu-id="fa749-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="fa749-117">Seu uso exclusivo é como um identificador que é fornecido como um parâmetro de `out` em uma chamada de método e que, por sua vez, pode ser passado para outros métodos para fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="fa749-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa749-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa749-118">Requirements</span></span>  
 <span data-ttu-id="fa749-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa749-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa749-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa749-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa749-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa749-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa749-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa749-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa749-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa749-123">See also</span></span>

- [<span data-ttu-id="fa749-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="fa749-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fa749-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="fa749-125">Debugging</span></span>](index.md)
