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
ms.openlocfilehash: 5064e66708044d82e3a097c8235b5b28a3412200
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077128"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="4c78d-102">Método IDebugAutoAttach::AutoAttach</span><span class="sxs-lookup"><span data-stu-id="4c78d-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="4c78d-103">Executa automaticamente o depurador de servidor chamado attach.</span><span class="sxs-lookup"><span data-stu-id="4c78d-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c78d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c78d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4c78d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c78d-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="4c78d-106">[in] Sempre definido como `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="4c78d-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="4c78d-107">[in] ID de processo, normalmente são recuperado com o `GetCurrentProcessId` função.</span><span class="sxs-lookup"><span data-stu-id="4c78d-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="4c78d-108">[in] Tipo de programa: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, ou `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="4c78d-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="4c78d-109">[in] ID do programa.</span><span class="sxs-lookup"><span data-stu-id="4c78d-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="4c78d-110">[in] A cadeia de caracteres passada pelo verbo debug.</span><span class="sxs-lookup"><span data-stu-id="4c78d-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c78d-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c78d-111">Return Value</span></span>  
 <span data-ttu-id="4c78d-112">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="4c78d-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c78d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c78d-113">Requirements</span></span>  
 <span data-ttu-id="4c78d-114">**Cabeçalho:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="4c78d-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c78d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c78d-115">See also</span></span>

- [<span data-ttu-id="4c78d-116">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="4c78d-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
