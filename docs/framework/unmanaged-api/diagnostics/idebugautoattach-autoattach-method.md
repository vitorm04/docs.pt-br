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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442118"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="e639d-102">Método IDebugAutoAttach::AutoAttach</span><span class="sxs-lookup"><span data-stu-id="e639d-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="e639d-103">Executa a anexação automática do depurador invocado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="e639d-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e639d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e639d-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e639d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e639d-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="e639d-106">no Sempre definido como `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="e639d-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="e639d-107">no ID do processo, normalmente recuperada com a `GetCurrentProcessId` função.</span><span class="sxs-lookup"><span data-stu-id="e639d-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="e639d-108">no Tipo de programa: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` ou `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="e639d-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="e639d-109">no ID do programa.</span><span class="sxs-lookup"><span data-stu-id="e639d-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="e639d-110">no Cadeia de caracteres passada pelo verbo Debug.</span><span class="sxs-lookup"><span data-stu-id="e639d-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e639d-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e639d-111">Return Value</span></span>  
 <span data-ttu-id="e639d-112">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="e639d-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e639d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e639d-113">Requirements</span></span>  
 <span data-ttu-id="e639d-114">**Cabeçalho:** DbgAutoAttach. h</span><span class="sxs-lookup"><span data-stu-id="e639d-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e639d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e639d-115">See also</span></span>

- [<span data-ttu-id="e639d-116">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="e639d-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
