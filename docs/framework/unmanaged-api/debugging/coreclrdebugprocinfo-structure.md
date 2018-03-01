---
title: Estrutura CoreClrDebugProcInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d341b875f9f64b9aa1fcdcf21668dafea0beac12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="f56f2-102">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="f56f2-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="f56f2-103">Representa um processo que está em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="f56f2-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f56f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f56f2-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="f56f2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f56f2-105">Members</span></span>  
  
|<span data-ttu-id="f56f2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f56f2-106">Member</span></span>|<span data-ttu-id="f56f2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f56f2-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="f56f2-108">Identificador de processo atribuída pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f56f2-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="f56f2-109">Identificador de processo que é atribuído pelo proxy de depuração remoto em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="f56f2-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="f56f2-110">Esse identificador é reciclado com menos frequência do que o identificador de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f56f2-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="f56f2-111">Linha de comando do processo.</span><span class="sxs-lookup"><span data-stu-id="f56f2-111">Command-line of the process.</span></span> <span data-ttu-id="f56f2-112">Esse membro pode ser truncado.</span><span class="sxs-lookup"><span data-stu-id="f56f2-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f56f2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f56f2-113">Requirements</span></span>  
 <span data-ttu-id="f56f2-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f56f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f56f2-115">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="f56f2-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f56f2-116">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f56f2-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f56f2-117">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f56f2-117">**.NET Framework Versions:** 3.5 SP1</span></span>
