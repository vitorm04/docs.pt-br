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
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795840"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="16deb-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="16deb-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="16deb-103">Indica se um intervalo específico de instruções nativas, representado por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="16deb-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16deb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16deb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="16deb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="16deb-105">Members</span></span>  
  
|<span data-ttu-id="16deb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="16deb-106">Member</span></span>|<span data-ttu-id="16deb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="16deb-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="16deb-108">O intervalo de instruções nativas não corresponde a nenhuma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="16deb-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="16deb-109">O intervalo de instruções nativas corresponde ao prólogo.</span><span class="sxs-lookup"><span data-stu-id="16deb-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="16deb-110">O intervalo de instruções nativas corresponde ao epílogo.</span><span class="sxs-lookup"><span data-stu-id="16deb-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16deb-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16deb-111">Requirements</span></span>  
 <span data-ttu-id="16deb-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16deb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16deb-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16deb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16deb-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16deb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16deb-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16deb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16deb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16deb-116">See also</span></span>

- [<span data-ttu-id="16deb-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="16deb-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="16deb-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="16deb-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
