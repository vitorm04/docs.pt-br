---
title: Método ICorDebugProcess2::GetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 015735e1c6c3b6c146f2fca3a9bdc28baeca2f92
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792515"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="ab32a-102">Método ICorDebugProcess2::GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="ab32a-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="ab32a-103">Obtém as configurações de sinalizador do compilador atual que o Common Language Runtime (CLR) usa para selecionar a imagem pré-compilada (ou seja, nativa) correta a ser carregada nesse processo.</span><span class="sxs-lookup"><span data-stu-id="ab32a-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab32a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab32a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab32a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab32a-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="ab32a-106">fora Um ponteiro para uma combinação de bits de valor de enumeração de [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) que são usados para selecionar a imagem pré-compilada correta a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="ab32a-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab32a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab32a-107">Remarks</span></span>  
 <span data-ttu-id="ab32a-108">Use o método [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) para definir os sinalizadores que o CLR usará para selecionar a imagem previamente compilada correta a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="ab32a-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab32a-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ab32a-109">Requirements</span></span>  
 <span data-ttu-id="ab32a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab32a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab32a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab32a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab32a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab32a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab32a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab32a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
