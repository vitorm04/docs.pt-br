---
title: Método ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790535"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="b3a6e-102">Método ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="b3a6e-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="b3a6e-103">Obtém um valor que indica se o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md) é conhecido por ter código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b3a6e-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a6e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3a6e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3a6e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3a6e-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="b3a6e-106">fora Um ponteiro para um valor booliano que indica se o processo tem código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b3a6e-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="b3a6e-107">O valor será `true` se o processo tiver código gerenciado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b3a6e-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3a6e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3a6e-108">Remarks</span></span>  
 <span data-ttu-id="b3a6e-109">Como a versão atual do `ICorPublishProcess` permite o acesso apenas a processos que têm código gerenciado, `IsManaged` sempre retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="b3a6e-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a6e-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b3a6e-110">Requirements</span></span>  
 <span data-ttu-id="b3a6e-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a6e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a6e-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b3a6e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b3a6e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3a6e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a6e-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a6e-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="b3a6e-115">See also</span></span>

- [<span data-ttu-id="b3a6e-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="b3a6e-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
