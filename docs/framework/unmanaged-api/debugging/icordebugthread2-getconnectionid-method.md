---
title: Método ICorDebugThread2::GetConnectionID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768975"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="f4b53-102">Método ICorDebugThread2::GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="f4b53-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="f4b53-103">Obtém o identificador de conexão para este objeto ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="f4b53-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4b53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4b53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4b53-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="f4b53-106">[out] Um `CONNID` que representa o identificador de conexão.</span><span class="sxs-lookup"><span data-stu-id="f4b53-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4b53-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4b53-107">Remarks</span></span>  
 <span data-ttu-id="f4b53-108">O `GetConnectionID` método retorna zero no `pdwConnectionId` parâmetro, se esse thread não é parte de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="f4b53-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="f4b53-109">Se esse thread está conectado a uma instância do Microsoft SQL Server 2005 Analysis Services (SSAS), o `CONNID` é mapeado para um identificador de processo do servidor (SPID).</span><span class="sxs-lookup"><span data-stu-id="f4b53-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b53-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4b53-110">Requirements</span></span>  
 <span data-ttu-id="f4b53-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4b53-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b53-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4b53-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4b53-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4b53-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4b53-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b53-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
