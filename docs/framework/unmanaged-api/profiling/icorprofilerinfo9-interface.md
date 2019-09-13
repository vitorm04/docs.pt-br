---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: af6bd02c6d4e88c72dca20d2520d1ecc8cf1c421
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928780"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="924a0-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="924a0-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="924a0-103">Uma subclasse de [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.</span><span class="sxs-lookup"><span data-stu-id="924a0-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="924a0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="924a0-104">Methods</span></span>  

| <span data-ttu-id="924a0-105">Método</span><span class="sxs-lookup"><span data-stu-id="924a0-105">Method</span></span>|<span data-ttu-id="924a0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="924a0-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="924a0-107">Método GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="924a0-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="924a0-108">Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.</span><span class="sxs-lookup"><span data-stu-id="924a0-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="924a0-109">Método GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="924a0-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="924a0-110">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="924a0-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="924a0-111">Método GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="924a0-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="924a0-112">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="924a0-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="924a0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="924a0-113">Requirements</span></span>  
<span data-ttu-id="924a0-114">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="924a0-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="924a0-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="924a0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="924a0-116">**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="924a0-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="924a0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="924a0-117">See also</span></span>

- [<span data-ttu-id="924a0-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="924a0-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
