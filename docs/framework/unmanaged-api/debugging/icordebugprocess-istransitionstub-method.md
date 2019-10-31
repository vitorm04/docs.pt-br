---
title: Método ICorDebugProcess::IsTransitionStub
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139393"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="0c3f4-102">Método ICorDebugProcess::IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="0c3f4-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="0c3f4-103">Obtém um valor que indica se um endereço está dentro de um stub que causará uma transição para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c3f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c3f4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c3f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c3f4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0c3f4-106">no Um valor `CORDB_ADDRESS` que especifica o endereço em questão.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="0c3f4-107">fora Um ponteiro para um valor booliano `true` se o endereço especificado estiver dentro de um stub que causará uma transição para o código gerenciado; caso contrário, \*`pbTransitionStub` será `false`.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c3f4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c3f4-108">Remarks</span></span>  
 <span data-ttu-id="0c3f4-109">O método `IsTransitionStub` pode ser usado por código de depuração não gerenciado para decidir quando retornar o controle de etapas para o stepper gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c3f4-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="0c3f4-110">Você também pode identificar stubs de transição examinando as informações no arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="0c3f4-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c3f4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c3f4-111">Requirements</span></span>  
 <span data-ttu-id="0c3f4-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c3f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c3f4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c3f4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c3f4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c3f4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c3f4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
