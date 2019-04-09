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
ms.openlocfilehash: 2f62707fb1e52a96cf3f131e9c11fee82ab03f4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097181"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="927e8-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="927e8-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="927e8-103">Indica se um determinado intervalo de instruções nativas, representada por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="927e8-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="927e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="927e8-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="927e8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="927e8-105">Members</span></span>  
  
|<span data-ttu-id="927e8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="927e8-106">Member</span></span>|<span data-ttu-id="927e8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="927e8-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="927e8-108">O intervalo de instruções nativas corresponde a qualquer região de código especial.</span><span class="sxs-lookup"><span data-stu-id="927e8-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="927e8-109">O intervalo de instruções nativas corresponde a prólogo.</span><span class="sxs-lookup"><span data-stu-id="927e8-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="927e8-110">O intervalo de instruções nativas corresponde a epílogo.</span><span class="sxs-lookup"><span data-stu-id="927e8-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="927e8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="927e8-111">Requirements</span></span>  
 <span data-ttu-id="927e8-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="927e8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="927e8-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="927e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="927e8-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="927e8-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="927e8-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="927e8-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="927e8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="927e8-116">See also</span></span>

- [<span data-ttu-id="927e8-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="927e8-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="927e8-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="927e8-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
