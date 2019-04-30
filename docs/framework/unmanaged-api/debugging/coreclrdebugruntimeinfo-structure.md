---
title: Estrutura CoreClrDebugRuntimeInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966036"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="a2aa8-102">Estrutura CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a2aa8-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="a2aa8-103">Representa uma instância de runtime (CLR) de linguagem comum que é carregada em um processo em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="a2aa8-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2aa8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2aa8-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a2aa8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a2aa8-105">Members</span></span>  
  
|<span data-ttu-id="a2aa8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a2aa8-106">Member</span></span>|<span data-ttu-id="a2aa8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2aa8-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="a2aa8-108">Identificador de tempo de execução que é atribuído pelo proxy de depuração remoto em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="a2aa8-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2aa8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2aa8-109">Requirements</span></span>  
 <span data-ttu-id="a2aa8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2aa8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2aa8-111">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a2aa8-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a2aa8-112">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a2aa8-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a2aa8-113">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a2aa8-113">**.NET Framework Versions:** 3.5 SP1</span></span>
