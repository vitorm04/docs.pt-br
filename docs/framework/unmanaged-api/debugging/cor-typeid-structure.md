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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273992"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="38694-102">Estrutura COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="38694-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="38694-103">Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="38694-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38694-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38694-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="38694-105">Membros</span><span class="sxs-lookup"><span data-stu-id="38694-105">Members</span></span>  
  
|<span data-ttu-id="38694-106">Membro</span><span class="sxs-lookup"><span data-stu-id="38694-106">Member</span></span>|<span data-ttu-id="38694-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="38694-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="38694-108">O primeiro token.</span><span class="sxs-lookup"><span data-stu-id="38694-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="38694-109">O segundo token.</span><span class="sxs-lookup"><span data-stu-id="38694-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38694-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="38694-110">Remarks</span></span>  
 <span data-ttu-id="38694-111">A `COR_TYPEID` estrutura é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="38694-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="38694-112">Em seguida, ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item.</span><span class="sxs-lookup"><span data-stu-id="38694-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="38694-113">Por exemplo, enumerando um objeto [ICorDebugHeapEnum](icordebugheapenum-interface.md) , você pode recuperar objetos [COR_HEAPOBJECT](cor-heapobject-structure.md) individuais que representam objetos individuais no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="38694-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="38694-114">Em seguida, você pode `COR_TYPEID` passar o valor `COR_HEAPOBJECT.type` do campo para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) para recuperar um objeto ICorDebugType que fornece informações de tipo sobre o objeto.</span><span class="sxs-lookup"><span data-stu-id="38694-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="38694-115">Um `COR_TYPEID` objeto deve ser opaco.</span><span class="sxs-lookup"><span data-stu-id="38694-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="38694-116">Seus campos individuais não devem ser acessados ou manipulados.</span><span class="sxs-lookup"><span data-stu-id="38694-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="38694-117">Seu uso exclusivo é como um identificador que é fornecido como um `out` parâmetro em uma chamada de método e que, por sua vez, pode ser passado para outros métodos para fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="38694-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38694-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38694-118">Requirements</span></span>  
 <span data-ttu-id="38694-119">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38694-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38694-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38694-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38694-121">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38694-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38694-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38694-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38694-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38694-123">See also</span></span>

- [<span data-ttu-id="38694-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="38694-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="38694-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="38694-125">Debugging</span></span>](index.md)
