---
title: Método ICorPublish::GetProcess
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790743"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="b9365-102">Método ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="b9365-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="b9365-103">Obtém uma instância de [ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="b9365-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9365-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9365-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9365-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9365-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="b9365-106">no O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="b9365-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b9365-107">fora Um ponteiro para o endereço de uma instância de `ICorPublishProcess` que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="b9365-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9365-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9365-108">Remarks</span></span>  
 <span data-ttu-id="b9365-109">`GetProcess` falhará se o processo não existir ou não for um processo gerenciado que possa ser depurado pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="b9365-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9365-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b9365-110">Requirements</span></span>  
 <span data-ttu-id="b9365-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9365-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9365-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b9365-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b9365-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9365-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9365-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9365-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9365-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9365-115">See also</span></span>

- [<span data-ttu-id="b9365-116">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="b9365-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
