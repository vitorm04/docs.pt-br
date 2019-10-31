---
title: Método ICorDebugProcess2::GetVersion
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 5f618f6779f6931785bba18f70fb1ac9baf46753
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137187"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="ab77d-102">Método ICorDebugProcess2::GetVersion</span><span class="sxs-lookup"><span data-stu-id="ab77d-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="ab77d-103">Obtém o número de versão do Common Language Runtime (CLR) que está em execução neste processo.</span><span class="sxs-lookup"><span data-stu-id="ab77d-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab77d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab77d-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="ab77d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab77d-105">Parameters</span></span>

`version`\
<span data-ttu-id="ab77d-106">fora Um ponteiro para uma estrutura COR_VERSION que armazena o número de versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ab77d-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab77d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab77d-107">Remarks</span></span>

<span data-ttu-id="ab77d-108">O método `GetVersion` retornará um código de erro se nenhum tempo de execução tiver sido carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="ab77d-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab77d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab77d-109">Requirements</span></span>

<span data-ttu-id="ab77d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab77d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ab77d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab77d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ab77d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab77d-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ab77d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab77d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
