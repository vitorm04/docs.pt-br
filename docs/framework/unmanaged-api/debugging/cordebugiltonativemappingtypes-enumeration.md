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
ms.openlocfilehash: ddb5af486ab6fb1c8c4fabf3ccf7b43d037e1eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789316"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="a593a-102">Enumeração CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="a593a-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="a593a-103">Indica se um intervalo específico de instruções nativas, representado por uma instância da estrutura COR_DEBUG_IL_TO_NATIVE_MAP, corresponde a uma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="a593a-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a593a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a593a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="a593a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a593a-105">Members</span></span>  
  
|<span data-ttu-id="a593a-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a593a-106">Member</span></span>|<span data-ttu-id="a593a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a593a-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="a593a-108">O intervalo de instruções nativas não corresponde a nenhuma região de código especial.</span><span class="sxs-lookup"><span data-stu-id="a593a-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="a593a-109">O intervalo de instruções nativas corresponde ao prólogo.</span><span class="sxs-lookup"><span data-stu-id="a593a-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="a593a-110">O intervalo de instruções nativas corresponde ao epílogo.</span><span class="sxs-lookup"><span data-stu-id="a593a-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a593a-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a593a-111">Requirements</span></span>  
 <span data-ttu-id="a593a-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a593a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a593a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a593a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a593a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a593a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a593a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a593a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a593a-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="a593a-116">See also</span></span>

- [<span data-ttu-id="a593a-117">Método GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="a593a-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="a593a-118">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a593a-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
