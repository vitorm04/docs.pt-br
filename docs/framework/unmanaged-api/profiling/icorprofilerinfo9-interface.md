---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 74031fd822550f8a0752d02ce0c2d89b2f5ae546
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444956"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="b653d-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="b653d-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="b653d-103">Uma subclasse de [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.</span><span class="sxs-lookup"><span data-stu-id="b653d-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="b653d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b653d-104">Methods</span></span>  

| <span data-ttu-id="b653d-105">Método</span><span class="sxs-lookup"><span data-stu-id="b653d-105">Method</span></span>|<span data-ttu-id="b653d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b653d-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="b653d-107">Método GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="b653d-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="b653d-108">Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.</span><span class="sxs-lookup"><span data-stu-id="b653d-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="b653d-109">Método GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="b653d-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="b653d-110">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="b653d-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="b653d-111">Método GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="b653d-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="b653d-112">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="b653d-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="b653d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b653d-113">Requirements</span></span>  
<span data-ttu-id="b653d-114">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b653d-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="b653d-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b653d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="b653d-116">**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b653d-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b653d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b653d-117">See also</span></span>

- [<span data-ttu-id="b653d-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b653d-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
