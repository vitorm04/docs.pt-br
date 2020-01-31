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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789190"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="c0a20-102">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="c0a20-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="c0a20-103">Cria uma conexão com um proxy de depurador que está sendo executado em um computador remoto e retorna um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que pode ser usado para consultar processos em execução e os tempos de execução carregados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="c0a20-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0a20-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a20-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0a20-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="c0a20-106">no Endereço IPv4 de um computador de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="c0a20-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="c0a20-107">fora Ponteiro para um ponteiro para um objeto [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) que será criado.</span><span class="sxs-lookup"><span data-stu-id="c0a20-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0a20-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c0a20-108">Return Value</span></span>  
 <span data-ttu-id="c0a20-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0a20-109">S_OK</span></span>  
 <span data-ttu-id="c0a20-110">O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="c0a20-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="c0a20-111">{1&gt;E_OUTOFMEMORY&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c0a20-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c0a20-112">Não é possível alocar memória suficiente para `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="c0a20-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="c0a20-113">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="c0a20-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c0a20-114">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="c0a20-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0a20-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c0a20-115">Requirements</span></span>  
 <span data-ttu-id="c0a20-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a20-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a20-117">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="c0a20-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c0a20-118">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="c0a20-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c0a20-119">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c0a20-119">**.NET Framework Versions:** 3.5 SP1</span></span>
