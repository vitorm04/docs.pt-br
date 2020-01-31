---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861639"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="8e794-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="8e794-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="8e794-103">Uma subclasse de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.</span><span class="sxs-lookup"><span data-stu-id="8e794-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="8e794-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8e794-104">Methods</span></span>  

| <span data-ttu-id="8e794-105">Método</span><span class="sxs-lookup"><span data-stu-id="8e794-105">Method</span></span>|<span data-ttu-id="8e794-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e794-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="8e794-107">Método GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="8e794-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="8e794-108">Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.</span><span class="sxs-lookup"><span data-stu-id="8e794-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="8e794-109">Método GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="8e794-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="8e794-110">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="8e794-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="8e794-111">Método GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="8e794-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="8e794-112">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="8e794-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="8e794-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8e794-113">Requirements</span></span>  
<span data-ttu-id="8e794-114">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="8e794-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="8e794-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8e794-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="8e794-116">**Versões do .net:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e794-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8e794-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="8e794-117">See also</span></span>

- [<span data-ttu-id="8e794-118">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8e794-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
