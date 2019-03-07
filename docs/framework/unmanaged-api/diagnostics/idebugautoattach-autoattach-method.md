---
title: Método IDebugAutoAttach::AutoAttach
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16ccc56579a1ebe45ada61a9565cc8ade335333d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469672"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="452df-102">Método IDebugAutoAttach::AutoAttach</span><span class="sxs-lookup"><span data-stu-id="452df-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="452df-103">Executa automaticamente o depurador de servidor chamado attach.</span><span class="sxs-lookup"><span data-stu-id="452df-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="452df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="452df-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="452df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="452df-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="452df-106">[in] Sempre definido como `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="452df-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="452df-107">[in] ID de processo, normalmente são recuperado com o `GetCurrentProcessId` função.</span><span class="sxs-lookup"><span data-stu-id="452df-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="452df-108">[in] Tipo de programa: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, ou `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="452df-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="452df-109">[in] ID do programa.</span><span class="sxs-lookup"><span data-stu-id="452df-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="452df-110">[in] A cadeia de caracteres passada pelo verbo debug.</span><span class="sxs-lookup"><span data-stu-id="452df-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="452df-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="452df-111">Return Value</span></span>  
 <span data-ttu-id="452df-112">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="452df-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="452df-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="452df-113">Requirements</span></span>  
 <span data-ttu-id="452df-114">**Cabeçalho:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="452df-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452df-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="452df-115">See also</span></span>
- [<span data-ttu-id="452df-116">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="452df-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
