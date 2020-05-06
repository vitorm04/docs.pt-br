---
title: Enumeração CorDebugHandleType
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 2d296c1778e00c4c72e860e0705994518d1481e8
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795869"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="7600e-102">Enumeração CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="7600e-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="7600e-103">Indica o tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="7600e-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7600e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7600e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="7600e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7600e-105">Members</span></span>  
  
|<span data-ttu-id="7600e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7600e-106">Member</span></span>|<span data-ttu-id="7600e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7600e-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="7600e-108">O identificador é forte, o que impede que um objeto seja recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7600e-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="7600e-109">O identificador é fraco, o que não impede que um objeto seja recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7600e-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="7600e-110">O identificador torna-se inválido quando o objeto é coletado.</span><span class="sxs-lookup"><span data-stu-id="7600e-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7600e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7600e-111">Requirements</span></span>  
 <span data-ttu-id="7600e-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7600e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7600e-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7600e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7600e-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7600e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7600e-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7600e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7600e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7600e-116">See also</span></span>

- [<span data-ttu-id="7600e-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="7600e-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
