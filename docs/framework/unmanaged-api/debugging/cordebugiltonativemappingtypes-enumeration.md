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
ms.openlocfilehash: 9fec0f4f31f45847dc092808b2d47c662213e9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402513"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="e7ef7-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="e7ef7-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="e7ef7-103">Indica se um determinado intervalo de instruções nativas, representado por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="e7ef7-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ef7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7ef7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="e7ef7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e7ef7-105">Members</span></span>  
  
|<span data-ttu-id="e7ef7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e7ef7-106">Member</span></span>|<span data-ttu-id="e7ef7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7ef7-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="e7ef7-108">O intervalo de instruções nativo não corresponde a nenhuma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="e7ef7-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="e7ef7-109">O intervalo de instruções nativas corresponde a prólogo.</span><span class="sxs-lookup"><span data-stu-id="e7ef7-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="e7ef7-110">O intervalo de instruções nativas corresponde ao epílogo.</span><span class="sxs-lookup"><span data-stu-id="e7ef7-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7ef7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7ef7-111">Requirements</span></span>  
 <span data-ttu-id="e7ef7-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7ef7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ef7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7ef7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7ef7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ef7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ef7-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ef7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ef7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7ef7-116">See Also</span></span>  
 [<span data-ttu-id="e7ef7-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="e7ef7-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="e7ef7-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="e7ef7-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
