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
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132161"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="00e82-102">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="00e82-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="00e82-103">Representa um processo que está sendo executado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="00e82-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00e82-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="00e82-105">Membros</span><span class="sxs-lookup"><span data-stu-id="00e82-105">Members</span></span>  
  
|<span data-ttu-id="00e82-106">Membro</span><span class="sxs-lookup"><span data-stu-id="00e82-106">Member</span></span>|<span data-ttu-id="00e82-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e82-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="00e82-108">Identificador de processo atribuído pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="00e82-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="00e82-109">Identificador de processo atribuído pelo proxy de depuração remota em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="00e82-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="00e82-110">Esse identificador recicla com menos frequência do que o identificador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="00e82-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="00e82-111">Linha de comando do processo.</span><span class="sxs-lookup"><span data-stu-id="00e82-111">Command-line of the process.</span></span> <span data-ttu-id="00e82-112">Esse membro pode estar truncado.</span><span class="sxs-lookup"><span data-stu-id="00e82-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00e82-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00e82-113">Requirements</span></span>  
 <span data-ttu-id="00e82-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e82-115">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="00e82-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="00e82-116">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="00e82-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="00e82-117">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="00e82-117">**.NET Framework Versions:** 3.5 SP1</span></span>
