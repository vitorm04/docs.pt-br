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
ms.openlocfilehash: 40dbfc60f8bde1198fd56a4a8aeed1dd6879d1ae
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795619"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="0549c-102">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="0549c-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="0549c-103">Representa um processo que está sendo executado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="0549c-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0549c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0549c-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="0549c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0549c-105">Members</span></span>  
  
|<span data-ttu-id="0549c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0549c-106">Member</span></span>|<span data-ttu-id="0549c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0549c-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="0549c-108">Identificador de processo atribuído pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0549c-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="0549c-109">Identificador de processo atribuído pelo proxy de depuração remota em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="0549c-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="0549c-110">Esse identificador recicla com menos frequência do que o identificador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0549c-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="0549c-111">Linha de comando do processo.</span><span class="sxs-lookup"><span data-stu-id="0549c-111">Command-line of the process.</span></span> <span data-ttu-id="0549c-112">Esse membro pode estar truncado.</span><span class="sxs-lookup"><span data-stu-id="0549c-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0549c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0549c-113">Requirements</span></span>  
 <span data-ttu-id="0549c-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0549c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0549c-115">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="0549c-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0549c-116">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="0549c-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0549c-117">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0549c-117">**.NET Framework Versions:** 3.5 SP1</span></span>
