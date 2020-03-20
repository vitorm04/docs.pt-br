---
title: Enumeração CREATE_ASM_NAME_OBJ_FLAGS
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: ee856dbd398d0fa5e3eee7d9b2b2cfc7c7a57ecf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176585"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="c54b5-102">Enumeração CREATE_ASM_NAME_OBJ_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c54b5-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="c54b5-103">Especifica os atributos de um objeto [IAssemblyName Interface](iassemblyname-interface.md) quando ele é construído pela função [CreateAssemblyNameObject.](createassemblynameobject-function.md)</span><span class="sxs-lookup"><span data-stu-id="c54b5-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c54b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c54b5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c54b5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c54b5-105">Members</span></span>  
  
|<span data-ttu-id="c54b5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c54b5-106">Member</span></span>|<span data-ttu-id="c54b5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c54b5-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="c54b5-108">Indica que o parâmetro passado é uma identidade textual.</span><span class="sxs-lookup"><span data-stu-id="c54b5-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="c54b5-109">Define alguns valores padrão.</span><span class="sxs-lookup"><span data-stu-id="c54b5-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="c54b5-110">Verifica a regra da assembléia do amigo (apenas nome e chave pública).</span><span class="sxs-lookup"><span data-stu-id="c54b5-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="c54b5-111">Este membro é apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="c54b5-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="c54b5-112">Uma combinação `CANOF_PARSE_DISPLAY_NAME` de `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bandeiras.</span><span class="sxs-lookup"><span data-stu-id="c54b5-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="c54b5-113">Este membro é apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="c54b5-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c54b5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c54b5-114">Requirements</span></span>  
 <span data-ttu-id="c54b5-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c54b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c54b5-116">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c54b5-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c54b5-117">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c54b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54b5-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="c54b5-118">See also</span></span>

- [<span data-ttu-id="c54b5-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c54b5-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c54b5-120">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="c54b5-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="c54b5-121">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="c54b5-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
