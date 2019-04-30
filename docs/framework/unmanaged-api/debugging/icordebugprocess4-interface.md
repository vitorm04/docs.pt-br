---
title: Interface ICorDebugProcess4
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948792"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="ae8ca-102">Interface ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="ae8ca-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="ae8ca-103">Fornece suporte para fora do controle de execução do processo.</span><span class="sxs-lookup"><span data-stu-id="ae8ca-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="ae8ca-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ae8ca-104">Methods</span></span>

| <span data-ttu-id="ae8ca-105">Método</span><span class="sxs-lookup"><span data-stu-id="ae8ca-105">Method</span></span>                                                                 | <span data-ttu-id="ae8ca-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae8ca-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ae8ca-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="ae8ca-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="ae8ca-108">Notifica o pipeline ICorDebug que fora do depurador de processo está continuando a execução do depurado.</span><span class="sxs-lookup"><span data-stu-id="ae8ca-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ae8ca-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae8ca-109">Remarks</span></span>

<span data-ttu-id="ae8ca-110">Essa interface reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ae8ca-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="ae8ca-111">No entanto, é uma interface COM que deriva de `IUnknown` com o GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` que pode ser obtido por meio de mecanismos COM usual.</span><span class="sxs-lookup"><span data-stu-id="ae8ca-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae8ca-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae8ca-112">Requirements</span></span>

<span data-ttu-id="ae8ca-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae8ca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ae8ca-114">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ae8ca-114">**Header:** None</span></span>

<span data-ttu-id="ae8ca-115">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="ae8ca-115">**Library:** None</span></span>

<span data-ttu-id="ae8ca-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae8ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8ca-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae8ca-117">See also</span></span>

- [<span data-ttu-id="ae8ca-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ae8ca-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ae8ca-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="ae8ca-119">Debugging</span></span>](index.md)
