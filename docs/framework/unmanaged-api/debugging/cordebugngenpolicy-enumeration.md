---
title: "Enumeração CorDebugNGenPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6042d5232995e68a4f59dfa68093446a03badfd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="4877d-102">Enumeração CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="4877d-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="4877d-103">Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="4877d-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4877d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4877d-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="4877d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="4877d-105">Members</span></span>  
  
|<span data-ttu-id="4877d-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="4877d-106">Member name</span></span>|<span data-ttu-id="4877d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4877d-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="4877d-108">Em um [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplicativo, o uso de imagens do cache de imagem nativa local está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="4877d-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="4877d-109">Em um aplicativo de área de trabalho, essa configuração não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="4877d-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4877d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4877d-110">Remarks</span></span>  
 <span data-ttu-id="4877d-111">O `CorDebugNGENPolicy` enumeração é usada pelo [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="4877d-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="4877d-112">Desabilitando o uso de imagens do cache de imagem nativa local fornece para uma experiência consistente de depuração, garantindo que o depurador carrega imagens depuráveis compilação JIT, em vez de imagens nativas otimizadas.</span><span class="sxs-lookup"><span data-stu-id="4877d-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4877d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4877d-113">Requirements</span></span>  
 <span data-ttu-id="4877d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4877d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4877d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4877d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4877d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4877d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4877d-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4877d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4877d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4877d-118">See Also</span></span>  
 [<span data-ttu-id="4877d-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="4877d-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
