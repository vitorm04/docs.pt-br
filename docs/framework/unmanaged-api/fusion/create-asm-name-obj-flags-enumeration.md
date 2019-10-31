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
ms.openlocfilehash: f6abb59c3aaec40a4e7b228b8c69147a2d454431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108876"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="0d8d5-102">Enumeração CREATE_ASM_NAME_OBJ_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0d8d5-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="0d8d5-103">Especifica os atributos de um objeto de [interface IAssemblyName](iassemblyname-interface.md) quando ele é construído pela função [CreateAssemblyNameObject](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0d8d5-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d8d5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0d8d5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0d8d5-105">Members</span></span>  
  
|<span data-ttu-id="0d8d5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0d8d5-106">Member</span></span>|<span data-ttu-id="0d8d5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d8d5-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="0d8d5-108">Indica que o parâmetro passado é uma identidade textual.</span><span class="sxs-lookup"><span data-stu-id="0d8d5-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="0d8d5-109">Define alguns valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0d8d5-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="0d8d5-110">Verifica a regra do assembly Friend (somente nome e chave pública).</span><span class="sxs-lookup"><span data-stu-id="0d8d5-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="0d8d5-111">Este membro é somente para uso interno.</span><span class="sxs-lookup"><span data-stu-id="0d8d5-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="0d8d5-112">Uma combinação dos sinalizadores `CANOF_PARSE_DISPLAY_NAME` e `CANOF_VERIFY_FRIEND_ASSEMBLYNAME`.</span><span class="sxs-lookup"><span data-stu-id="0d8d5-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="0d8d5-113">Este membro é somente para uso interno.</span><span class="sxs-lookup"><span data-stu-id="0d8d5-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d8d5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d8d5-114">Requirements</span></span>  
 <span data-ttu-id="0d8d5-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d8d5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d8d5-116">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0d8d5-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0d8d5-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d8d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8d5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d8d5-118">See also</span></span>

- [<span data-ttu-id="0d8d5-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="0d8d5-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="0d8d5-120">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="0d8d5-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="0d8d5-121">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="0d8d5-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
