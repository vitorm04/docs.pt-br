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
ms.openlocfilehash: d52757f82a950c382c7c8f2162630eda7d7795e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132099"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="bae0e-102">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="bae0e-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="bae0e-103">Cria uma conexão com um proxy de depurador que está sendo executado em um computador remoto e retorna um objeto [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) que pode ser usado para consultar processos em execução e os tempos de execução carregados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="bae0e-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bae0e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bae0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bae0e-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="bae0e-106">no Endereço IPv4 de um computador de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="bae0e-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="bae0e-107">fora Ponteiro para um ponteiro para um objeto [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) que será criado.</span><span class="sxs-lookup"><span data-stu-id="bae0e-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bae0e-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bae0e-108">Return Value</span></span>  
 <span data-ttu-id="bae0e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="bae0e-109">S_OK</span></span>  
 <span data-ttu-id="bae0e-110">O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="bae0e-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="bae0e-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bae0e-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="bae0e-112">Não é possível alocar memória suficiente para `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="bae0e-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="bae0e-113">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="bae0e-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bae0e-114">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="bae0e-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae0e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bae0e-115">Requirements</span></span>  
 <span data-ttu-id="bae0e-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae0e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae0e-117">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="bae0e-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="bae0e-118">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="bae0e-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="bae0e-119">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="bae0e-119">**.NET Framework Versions:** 3.5 SP1</span></span>
