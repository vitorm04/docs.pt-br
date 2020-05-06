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
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860935"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="3b11b-102">Estrutura CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="3b11b-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="3b11b-103">Representa uma instância de Common Language Runtime (CLR) que é carregada em um processo em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="3b11b-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b11b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b11b-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="3b11b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3b11b-105">Members</span></span>  
  
|<span data-ttu-id="3b11b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3b11b-106">Member</span></span>|<span data-ttu-id="3b11b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b11b-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="3b11b-108">Identificador de tempo de execução atribuído pelo proxy de depuração remota em execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="3b11b-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b11b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b11b-109">Requirements</span></span>  
 <span data-ttu-id="3b11b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b11b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b11b-111">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="3b11b-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3b11b-112">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="3b11b-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3b11b-113">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3b11b-113">**.NET Framework Versions:** 3.5 SP1</span></span>
