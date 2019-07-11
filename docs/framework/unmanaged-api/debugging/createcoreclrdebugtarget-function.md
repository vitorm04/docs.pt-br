---
title: Função CreateCoreClrDebugTarget
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739296"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="391b8-102">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="391b8-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="391b8-103">Cria uma conexão a um proxy de depurador que está em execução em um computador remoto e retorna um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto que pode ser usado para consultar os processos em execução e tempos de execução carregados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="391b8-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="391b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="391b8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="391b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="391b8-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="391b8-106">[in] Endereço IPv4 de uma máquina de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="391b8-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="391b8-107">[out] Ponteiro para um ponteiro para um [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="391b8-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="391b8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="391b8-108">Return Value</span></span>  
 <span data-ttu-id="391b8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="391b8-109">S_OK</span></span>  
 <span data-ttu-id="391b8-110">O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.</span><span class="sxs-lookup"><span data-stu-id="391b8-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="391b8-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="391b8-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="391b8-112">Não é possível alocar memória suficiente para `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="391b8-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="391b8-113">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="391b8-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="391b8-114">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="391b8-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="391b8-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="391b8-115">Requirements</span></span>  
 <span data-ttu-id="391b8-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="391b8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="391b8-117">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="391b8-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="391b8-118">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="391b8-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="391b8-119">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="391b8-119">**.NET Framework Versions:** 3.5 SP1</span></span>
