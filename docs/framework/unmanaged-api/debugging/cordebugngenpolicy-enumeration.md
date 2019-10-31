---
title: Enumeração CorDebugNGenPolicy
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097869"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="650f0-102">Enumeração CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="650f0-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="650f0-103">Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="650f0-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="650f0-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="650f0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="650f0-105">Members</span></span>  
  
|<span data-ttu-id="650f0-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="650f0-106">Member name</span></span>|<span data-ttu-id="650f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="650f0-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="650f0-108">Em um aplicativo [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)], o uso de imagens do cache de imagem nativa local está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="650f0-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="650f0-109">Em um aplicativo de área de trabalho, essa configuração não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="650f0-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="650f0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="650f0-110">Remarks</span></span>  
 <span data-ttu-id="650f0-111">A enumeração de `CorDebugNGENPolicy` é usada pelo método [ICorDebugProcess5:: EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="650f0-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="650f0-112">A desabilitação do uso de imagens do cache de imagem nativa local fornece uma experiência de depuração consistente, garantindo que o depurador Carregue imagens depurável compiladas por JIT em vez de imagens nativas otimizadas.</span><span class="sxs-lookup"><span data-stu-id="650f0-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650f0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="650f0-113">Requirements</span></span>  
 <span data-ttu-id="650f0-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650f0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="650f0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="650f0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="650f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="650f0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650f0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="650f0-118">See also</span></span>

- [<span data-ttu-id="650f0-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="650f0-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
