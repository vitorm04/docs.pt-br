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
ms.openlocfilehash: c83bdcca4fab75b4ae94500ceb785b6000cd802a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860871"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="a4518-102">Função CreateDebuggingInterfaceFromVersion para Silverlight</span><span class="sxs-lookup"><span data-stu-id="a4518-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="a4518-103">Aceita uma cadeia de caracteres de versão Common Language Runtime (CLR) retornada da [função CreateVersionStringFromModule](createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente (normalmente, [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a4518-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4518-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4518-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4518-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4518-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="a4518-106">no Cadeia de caracteres da versão do CLR no depurador de destino, que é retornada pela [função CreateVersionStringFromModule](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="a4518-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a4518-107">fora Ponteiro para um ponteiro para um objeto COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="a4518-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="a4518-108">Esse objeto será convertido em um objeto [ICorDebug](icordebug-interface.md) antes de ser retornado.</span><span class="sxs-lookup"><span data-stu-id="a4518-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4518-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a4518-109">Return Value</span></span>  
 <span data-ttu-id="a4518-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4518-110">S_OK</span></span>  
 <span data-ttu-id="a4518-111">`ppCordb`faz referência a um objeto válido que implementa a interface de [interface ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a4518-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a4518-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4518-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="a4518-113">`szDebuggeeVersion` Ou `ppCordb` é nulo.</span><span class="sxs-lookup"><span data-stu-id="a4518-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="a4518-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="a4518-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="a4518-115">Não é possível localizar um componente necessário para a depuração CLR.</span><span class="sxs-lookup"><span data-stu-id="a4518-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="a4518-116">Isso significa que o MSCorDbi. dll ou o mscordaccore. dll não foi encontrado no mesmo diretório que o CoreCLR. dll de destino.</span><span class="sxs-lookup"><span data-stu-id="a4518-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a4518-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="a4518-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="a4518-118">MSCorDbi. dll ou mscordaccore. dll não é a mesma versão que o CoreCLR. dll de destino.</span><span class="sxs-lookup"><span data-stu-id="a4518-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a4518-119">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="a4518-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a4518-120">Não é possível retornar uma [interface ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a4518-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4518-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4518-121">Remarks</span></span>  
 <span data-ttu-id="a4518-122">A interface retornada fornece os recursos para anexar a um CLR em um processo de destino e depurar o código gerenciado que o CLR está executando.</span><span class="sxs-lookup"><span data-stu-id="a4518-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4518-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4518-123">Requirements</span></span>  
 <span data-ttu-id="a4518-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4518-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4518-125">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="a4518-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a4518-126">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="a4518-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a4518-127">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a4518-127">**.NET Framework Versions:** 3.5 SP1</span></span>
