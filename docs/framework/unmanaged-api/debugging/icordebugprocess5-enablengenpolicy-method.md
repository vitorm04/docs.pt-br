---
title: Método ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca656aeba04526164a65760af990455965c5288e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665208"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="3c0b2-102">Método ICorDebugProcess5::EnableNGENPolicy</span><span class="sxs-lookup"><span data-stu-id="3c0b2-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="3c0b2-103">Define um valor que determina como um aplicativo carrega as imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c0b2-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c0b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c0b2-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="3c0b2-106">[in] Um [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constante que determina como um aplicativo carrega as imagens nativas durante a execução em um depurador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c0b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c0b2-107">Remarks</span></span>  
 <span data-ttu-id="3c0b2-108">Se a política está definida com êxito, o método retorna `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="3c0b2-109">Se `ePolicy` está fora do intervalo dos valores enumerados definido por [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), o método retorna `E_INVALIDARG` e a chamada de método não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="3c0b2-110">Se a política do gerador de imagem nativa (Ngen.exe) não pode ser atualizada, o método retorna `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="3c0b2-111">O `ICorDebugProcess5::EnableNGenPolicy` método pode ser chamado a qualquer momento durante o tempo de vida do processo.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="3c0b2-112">A política está em vigor para todos os módulos que são carregados depois que a política está definida.</span><span class="sxs-lookup"><span data-stu-id="3c0b2-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0b2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c0b2-113">Requirements</span></span>  
 <span data-ttu-id="3c0b2-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0b2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c0b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c0b2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c0b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c0b2-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0b2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c0b2-118">See also</span></span>
- [<span data-ttu-id="3c0b2-119">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="3c0b2-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="3c0b2-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3c0b2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3c0b2-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="3c0b2-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
