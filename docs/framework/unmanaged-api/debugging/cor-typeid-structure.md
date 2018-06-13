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
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408334"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="5128a-102">Estrutura COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="5128a-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="5128a-103">Contém um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="5128a-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5128a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5128a-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="5128a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5128a-105">Members</span></span>  
  
|<span data-ttu-id="5128a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5128a-106">Member</span></span>|<span data-ttu-id="5128a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5128a-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="5128a-108">O primeiro token.</span><span class="sxs-lookup"><span data-stu-id="5128a-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="5128a-109">O segundo token.</span><span class="sxs-lookup"><span data-stu-id="5128a-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5128a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5128a-110">Remarks</span></span>  
 <span data-ttu-id="5128a-111">O `COR_TYPEID` estrutura é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="5128a-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="5128a-112">Ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item.</span><span class="sxs-lookup"><span data-stu-id="5128a-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="5128a-113">Por exemplo, enumerando uma [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) do objeto, você pode recuperar individuais [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos que representam objetos individuais no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5128a-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="5128a-114">Você pode passar o `COR_TYPEID` o valor do `COR_HEAPOBJECT.type` campo para o [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) método para recuperar um objeto de ICorDebugType que fornece informações sobre o objeto de tipo.</span><span class="sxs-lookup"><span data-stu-id="5128a-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="5128a-115">Um `COR_TYPEID` objeto deve ser opaco.</span><span class="sxs-lookup"><span data-stu-id="5128a-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="5128a-116">Seus campos individuais não devem ser acessados ou manipulados.</span><span class="sxs-lookup"><span data-stu-id="5128a-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="5128a-117">Seu uso exclusivo é como um identificador que é fornecido como um `out` parâmetro em uma chamada de método e que pode, por sua vez, ser passado para outros métodos para fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5128a-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5128a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5128a-118">Requirements</span></span>  
 <span data-ttu-id="5128a-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5128a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5128a-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5128a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5128a-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5128a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5128a-122">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5128a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5128a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5128a-123">See Also</span></span>  
 [<span data-ttu-id="5128a-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="5128a-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="5128a-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="5128a-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
