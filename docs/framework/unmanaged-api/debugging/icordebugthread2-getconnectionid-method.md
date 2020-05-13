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
ms.openlocfilehash: c630daa50d465622c421381ac080eaa8d9d8d01d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379071"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="b777c-102">Método ICorDebugThread2::GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="b777c-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="b777c-103">Obtém o identificador de conexão para este objeto ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="b777c-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b777c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b777c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b777c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b777c-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="b777c-106">fora Um `CONNID` que representa o identificador de conexão.</span><span class="sxs-lookup"><span data-stu-id="b777c-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b777c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b777c-107">Remarks</span></span>  
 <span data-ttu-id="b777c-108">O `GetConnectionID` método retornará zero no `pdwConnectionId` parâmetro, se esse thread não fizer parte de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="b777c-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="b777c-109">Se esse thread estiver conectado a uma instância do Microsoft SQL Server 2005 Analysis Services (SSAS), o `CONNID` será mapeado para um identificador de processo do servidor (SPID).</span><span class="sxs-lookup"><span data-stu-id="b777c-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b777c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b777c-110">Requirements</span></span>  
 <span data-ttu-id="b777c-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b777c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b777c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b777c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b777c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b777c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b777c-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b777c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
