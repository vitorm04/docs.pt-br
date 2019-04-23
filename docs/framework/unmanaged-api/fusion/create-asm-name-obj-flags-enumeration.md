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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aebc6dfe4830e6477cda8fd279b8ef2a8040895c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149663"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="1e279-102">Enumeração CREATE_ASM_NAME_OBJ_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1e279-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="1e279-103">Especifica os atributos de um [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) do objeto quando ele é construído pela [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="1e279-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e279-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e279-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="1e279-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1e279-105">Members</span></span>  
  
|<span data-ttu-id="1e279-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1e279-106">Member</span></span>|<span data-ttu-id="1e279-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e279-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="1e279-108">Indica que o parâmetro passado é uma identidade textual.</span><span class="sxs-lookup"><span data-stu-id="1e279-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="1e279-109">Define alguns valores padrão.</span><span class="sxs-lookup"><span data-stu-id="1e279-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="1e279-110">Verifica a regra de assembly friend (somente o nome e a chave pública).</span><span class="sxs-lookup"><span data-stu-id="1e279-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="1e279-111">Esse membro é apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="1e279-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="1e279-112">Uma combinação da `CANOF_PARSE_DISPLAY_NAME` e `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="1e279-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="1e279-113">Esse membro é apenas para uso interno.</span><span class="sxs-lookup"><span data-stu-id="1e279-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e279-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e279-114">Requirements</span></span>  
 <span data-ttu-id="1e279-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e279-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e279-116">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1e279-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1e279-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e279-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e279-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e279-118">See also</span></span>

- [<span data-ttu-id="1e279-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="1e279-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="1e279-120">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="1e279-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [<span data-ttu-id="1e279-121">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="1e279-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
