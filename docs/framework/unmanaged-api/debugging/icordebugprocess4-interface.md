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
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213576"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="3a5cb-102">Interface ICorDebugProcess4</span><span class="sxs-lookup"><span data-stu-id="3a5cb-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="3a5cb-103">Fornece suporte para controle de execução fora do processo.</span><span class="sxs-lookup"><span data-stu-id="3a5cb-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="3a5cb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a5cb-104">Methods</span></span>

| <span data-ttu-id="3a5cb-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a5cb-105">Method</span></span>                                                                 | <span data-ttu-id="3a5cb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a5cb-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="3a5cb-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="3a5cb-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="3a5cb-108">Notifica o pipeline ICorDebug que o depurador fora do processo está continuando a execução do depurador.</span><span class="sxs-lookup"><span data-stu-id="3a5cb-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3a5cb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a5cb-109">Remarks</span></span>

<span data-ttu-id="3a5cb-110">Essa interface reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="3a5cb-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="3a5cb-111">No entanto, é uma interface COM que deriva de `IUnknown` com GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` que pode ser obtido por meio dos mecanismos com usuais.</span><span class="sxs-lookup"><span data-stu-id="3a5cb-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a5cb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a5cb-112">Requirements</span></span>

<span data-ttu-id="3a5cb-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a5cb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3a5cb-114">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="3a5cb-114">**Header:** None</span></span>

<span data-ttu-id="3a5cb-115">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="3a5cb-115">**Library:** None</span></span>

<span data-ttu-id="3a5cb-116">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a5cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3a5cb-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a5cb-117">See also</span></span>

- [<span data-ttu-id="3a5cb-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3a5cb-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3a5cb-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="3a5cb-119">Debugging</span></span>](index.md)
