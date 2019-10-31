---
title: Enumeração CorDebugIlToNativeMappingTypes
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 949d04fe8d9ce492fb320fb4732677ffb35302ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132821"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="e8179-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="e8179-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="e8179-103">Indica se um intervalo específico de instruções nativas, representado por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="e8179-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8179-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8179-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="e8179-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e8179-105">Members</span></span>  
  
|<span data-ttu-id="e8179-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e8179-106">Member</span></span>|<span data-ttu-id="e8179-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8179-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="e8179-108">O intervalo de instruções nativas não corresponde a nenhuma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="e8179-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="e8179-109">O intervalo de instruções nativas corresponde ao prólogo.</span><span class="sxs-lookup"><span data-stu-id="e8179-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="e8179-110">O intervalo de instruções nativas corresponde ao epílogo.</span><span class="sxs-lookup"><span data-stu-id="e8179-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8179-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8179-111">Requirements</span></span>  
 <span data-ttu-id="e8179-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8179-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8179-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8179-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8179-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8179-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8179-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8179-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8179-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8179-116">See also</span></span>

- [<span data-ttu-id="e8179-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="e8179-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="e8179-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="e8179-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
