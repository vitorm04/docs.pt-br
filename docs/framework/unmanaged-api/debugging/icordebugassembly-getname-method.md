---
title: Método ICorDebugAssembly::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127164"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="38888-102">Método ICorDebugAssembly::GetName</span><span class="sxs-lookup"><span data-stu-id="38888-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="38888-103">Obtém o nome do assembly que essa instância de `ICorDebugAssembly` representa.</span><span class="sxs-lookup"><span data-stu-id="38888-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38888-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38888-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38888-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38888-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="38888-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="38888-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="38888-107">fora Um ponteiro para um inteiro que especifica o comprimento real do nome.</span><span class="sxs-lookup"><span data-stu-id="38888-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="38888-108">fora Uma matriz que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="38888-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38888-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="38888-109">Remarks</span></span>  
 <span data-ttu-id="38888-110">O método `GetName` retorna o caminho completo e o nome do arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="38888-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38888-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38888-111">Requirements</span></span>  
 <span data-ttu-id="38888-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38888-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38888-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38888-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38888-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38888-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38888-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38888-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
