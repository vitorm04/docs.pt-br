---
title: Estrutura StackOverflowInfo
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006513"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="65204-102">Estrutura StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="65204-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="65204-103">Armazena o tipo de estouro que ocorreu e informações sobre a exceção que foi lançada devido ao estouro.</span><span class="sxs-lookup"><span data-stu-id="65204-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65204-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65204-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="65204-105">Membros</span><span class="sxs-lookup"><span data-stu-id="65204-105">Members</span></span>  
  
|<span data-ttu-id="65204-106">Membro</span><span class="sxs-lookup"><span data-stu-id="65204-106">Member</span></span>|<span data-ttu-id="65204-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="65204-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="65204-108">Um valor da enumeração [StackOverflowType](stackoverflowtype-enumeration.md) que especifica o tipo de estouro.</span><span class="sxs-lookup"><span data-stu-id="65204-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="65204-109">Um ponteiro para um `EXCEPTION_POINTERS` objeto Win32, que contém um registro de exceção com uma descrição independente de computador de uma exceção e um registro de contexto com uma descrição dependente de computador do contexto do processador no momento da exceção.</span><span class="sxs-lookup"><span data-stu-id="65204-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65204-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="65204-110">Remarks</span></span>  
 <span data-ttu-id="65204-111">Um `StackOverflowInfo` objeto é passado para o método [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) para `Event_StackOverflow` eventos.</span><span class="sxs-lookup"><span data-stu-id="65204-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65204-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65204-112">Requirements</span></span>  
 <span data-ttu-id="65204-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65204-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65204-114">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="65204-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="65204-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65204-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65204-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65204-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65204-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="65204-117">See also</span></span>

- [<span data-ttu-id="65204-118">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="65204-118">Hosting Structures</span></span>](hosting-structures.md)
