---
title: "Função CreateCoreClrDebugTarget"
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
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="6100d-102">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="6100d-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="6100d-103">Cria uma conexão a um proxy do depurador que está sendo executado em um computador remoto e retorna um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto que pode ser usado para consultar os processos em execução e os tempos de execução carregados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="6100d-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6100d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6100d-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6100d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6100d-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="6100d-106">[in] Endereço IPv4 de um computador de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="6100d-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="6100d-107">[out] Ponteiro para um ponteiro para um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="6100d-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6100d-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6100d-108">Return Value</span></span>  
 <span data-ttu-id="6100d-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6100d-109">S_OK</span></span>  
 <span data-ttu-id="6100d-110">O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.</span><span class="sxs-lookup"><span data-stu-id="6100d-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="6100d-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6100d-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="6100d-112">Não é possível alocar memória suficiente para `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="6100d-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="6100d-113">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="6100d-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="6100d-114">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="6100d-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6100d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6100d-115">Requirements</span></span>  
 <span data-ttu-id="6100d-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6100d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6100d-117">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="6100d-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="6100d-118">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="6100d-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="6100d-119">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="6100d-119">**.NET Framework Versions:** 3.5 SP1</span></span>
