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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61b57d534770c6ab7cacbc2c084ac364dc31863f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717604"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="3a1f0-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="3a1f0-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="3a1f0-103">Indica se um determinado intervalo de instruções nativas, representada por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a1f0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="3a1f0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3a1f0-105">Members</span></span>  
  
|<span data-ttu-id="3a1f0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3a1f0-106">Member</span></span>|<span data-ttu-id="3a1f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a1f0-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="3a1f0-108">O intervalo de instruções nativas corresponde a qualquer região de código especial.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="3a1f0-109">O intervalo de instruções nativas corresponde a prólogo.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="3a1f0-110">O intervalo de instruções nativas corresponde a epílogo.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a1f0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a1f0-111">Requirements</span></span>  
 <span data-ttu-id="3a1f0-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1f0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a1f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a1f0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a1f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a1f0-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1f0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a1f0-116">See also</span></span>
- [<span data-ttu-id="3a1f0-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="3a1f0-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="3a1f0-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="3a1f0-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
