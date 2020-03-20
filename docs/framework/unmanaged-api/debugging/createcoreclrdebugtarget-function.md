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
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179213"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="3355c-102">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="3355c-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="3355c-103">Cria uma conexão com um proxy dede-depurador que está sendo executado em uma máquina remota e retorna um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que pode ser usado para consultar processos em execução e tempos de execução carregados na máquina remota.</span><span class="sxs-lookup"><span data-stu-id="3355c-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3355c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3355c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3355c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="3355c-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="3355c-106">[em] Endereço IPv4 de uma máquina alvo remota.</span><span class="sxs-lookup"><span data-stu-id="3355c-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="3355c-107">[fora] Ponteiro para um ponteiro para um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que será criado.</span><span class="sxs-lookup"><span data-stu-id="3355c-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3355c-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3355c-108">Return Value</span></span>  
 <span data-ttu-id="3355c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="3355c-109">S_OK</span></span>  
 <span data-ttu-id="3355c-110">O número de CLRs no processo foi determinado com sucesso, e as matrizes de cabo e caminho correspondentes foram devidamente preenchidas.</span><span class="sxs-lookup"><span data-stu-id="3355c-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="3355c-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3355c-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3355c-112">Não é possível `ppTarget`alocar memória suficiente para .</span><span class="sxs-lookup"><span data-stu-id="3355c-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="3355c-113">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="3355c-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3355c-114">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="3355c-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3355c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3355c-115">Requirements</span></span>  
 <span data-ttu-id="3355c-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3355c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3355c-117">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="3355c-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3355c-118">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="3355c-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3355c-119">**.NET Framework Versões:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="3355c-119">**.NET Framework Versions:** 3.5 SP1</span></span>
