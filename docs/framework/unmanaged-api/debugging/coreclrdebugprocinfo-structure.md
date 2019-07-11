---
title: Estrutura CoreClrDebugProcInfo
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fc34add4038d25d60e4728847e0d84914a14e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739420"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="e8e38-102">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="e8e38-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="e8e38-103">Representa um processo que está em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="e8e38-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8e38-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="e8e38-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e8e38-105">Members</span></span>  
  
|<span data-ttu-id="e8e38-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e8e38-106">Member</span></span>|<span data-ttu-id="e8e38-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8e38-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="e8e38-108">Identificador do processo atribuída pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e8e38-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="e8e38-109">Identificador de processo que é atribuído pelo proxy de depuração remoto em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="e8e38-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="e8e38-110">Esse identificador é reciclado com menos frequência do que o identificador de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e8e38-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="e8e38-111">Linha de comando do processo.</span><span class="sxs-lookup"><span data-stu-id="e8e38-111">Command-line of the process.</span></span> <span data-ttu-id="e8e38-112">Esse membro pode ser truncado.</span><span class="sxs-lookup"><span data-stu-id="e8e38-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8e38-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8e38-113">Requirements</span></span>  
 <span data-ttu-id="e8e38-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e38-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e38-115">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e8e38-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e8e38-116">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e8e38-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e8e38-117">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e8e38-117">**.NET Framework Versions:** 3.5 SP1</span></span>
