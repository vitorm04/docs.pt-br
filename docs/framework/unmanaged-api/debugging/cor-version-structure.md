---
title: Estrutura COR_VERSION
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274180"
---
# <a name="cor_version-structure"></a><span data-ttu-id="26b7a-102">Estrutura COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="26b7a-102">COR_VERSION Structure</span></span>
<span data-ttu-id="26b7a-103">Armazena o número da versão com quatro partes padrão do CLR.</span><span class="sxs-lookup"><span data-stu-id="26b7a-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26b7a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="26b7a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="26b7a-105">Members</span></span>  
  
|<span data-ttu-id="26b7a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="26b7a-106">Member</span></span>|<span data-ttu-id="26b7a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="26b7a-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="26b7a-108">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="26b7a-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="26b7a-109">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="26b7a-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="26b7a-110">O número de build.</span><span class="sxs-lookup"><span data-stu-id="26b7a-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="26b7a-111">O número da subcompilação.</span><span class="sxs-lookup"><span data-stu-id="26b7a-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26b7a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="26b7a-112">Remarks</span></span>  
 <span data-ttu-id="26b7a-113">Se o número de versão for 1.0.3705.288, 1 será o número de versão principal, 0 é o número de versão secundária, 3705 é o número da compilação e 288 é o número da subcompilação.</span><span class="sxs-lookup"><span data-stu-id="26b7a-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b7a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26b7a-114">Requirements</span></span>  
 <span data-ttu-id="26b7a-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b7a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b7a-116">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="26b7a-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="26b7a-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b7a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b7a-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b7a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b7a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26b7a-119">See also</span></span>

- [<span data-ttu-id="26b7a-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="26b7a-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="26b7a-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="26b7a-121">Debugging</span></span>](index.md)
