---
title: Função CreateDebuggingInterfaceFromVersion para Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53571268391011cc1dc0ff112d484e1fa140057f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407708"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="a99b3-102">Função CreateDebuggingInterfaceFromVersion para Silverlight</span><span class="sxs-lookup"><span data-stu-id="a99b3-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="a99b3-103">Aceita uma cadeia de versão de tempo de execução (CLR) linguagem comum que é retornada o [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente (normalmente, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a99b3-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a99b3-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a99b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a99b3-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="a99b3-106">[in] Cadeia de caracteres de versão do CLR no depurador de destino, que é retornado pelo [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="a99b3-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a99b3-107">[out] Ponteiro para um ponteiro para um objeto COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="a99b3-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="a99b3-108">Esse objeto será convertido em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto antes de ser retornado.</span><span class="sxs-lookup"><span data-stu-id="a99b3-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a99b3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a99b3-109">Return Value</span></span>  
 <span data-ttu-id="a99b3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a99b3-110">S_OK</span></span>  
 <span data-ttu-id="a99b3-111">`ppCordb` referencia um objeto que implementa o [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a99b3-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a99b3-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a99b3-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="a99b3-113">O `szDebuggeeVersion` ou `ppCordb` é nulo.</span><span class="sxs-lookup"><span data-stu-id="a99b3-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="a99b3-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="a99b3-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="a99b3-115">Um componente necessário para a depuração CLR não pode ser localizado.</span><span class="sxs-lookup"><span data-stu-id="a99b3-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="a99b3-116">Isso significa que o mscordbi.dll ou mscordaccore.dll não foi encontrado no mesmo diretório que o destino CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="a99b3-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a99b3-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="a99b3-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="a99b3-118">Mscordbi.dll ou mscordaccore.dll não é a mesma versão do CoreCLR. dll de destino.</span><span class="sxs-lookup"><span data-stu-id="a99b3-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a99b3-119">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="a99b3-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a99b3-120">Não é possível retornar um [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a99b3-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a99b3-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="a99b3-121">Remarks</span></span>  
 <span data-ttu-id="a99b3-122">A interface que é retornada fornece os recursos para anexar a um CLR em um processo de destino e depurar o código gerenciado que está executando o CLR.</span><span class="sxs-lookup"><span data-stu-id="a99b3-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a99b3-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a99b3-123">Requirements</span></span>  
 <span data-ttu-id="a99b3-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a99b3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a99b3-125">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="a99b3-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a99b3-126">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="a99b3-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a99b3-127">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a99b3-127">**.NET Framework Versions:** 3.5 SP1</span></span>
