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
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208618"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="7565c-102">Função CreateDebuggingInterfaceFromVersion para Silverlight</span><span class="sxs-lookup"><span data-stu-id="7565c-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="7565c-103">Aceita uma cadeia de caracteres de versão Common Language Runtime (CLR) retornada da [função CreateVersionStringFromModule](createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente (normalmente, [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="7565c-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7565c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7565c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7565c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7565c-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="7565c-106">no Cadeia de caracteres da versão do CLR no depurador de destino, que é retornada pela [função CreateVersionStringFromModule](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="7565c-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="7565c-107">fora Ponteiro para um ponteiro para um objeto COM ( `IUnknown` ).</span><span class="sxs-lookup"><span data-stu-id="7565c-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="7565c-108">Esse objeto será convertido em um objeto [ICorDebug](icordebug-interface.md) antes de ser retornado.</span><span class="sxs-lookup"><span data-stu-id="7565c-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7565c-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7565c-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="7565c-110">`ppCordb`faz referência a um objeto válido que implementa a interface de [interface ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7565c-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="7565c-111">`szDebuggeeVersion`Ou `ppCordb` é nulo.</span><span class="sxs-lookup"><span data-stu-id="7565c-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="7565c-112">Não é possível localizar um componente necessário para a depuração CLR.</span><span class="sxs-lookup"><span data-stu-id="7565c-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="7565c-113">O _MSCorDbi. dll_ ou o _mscordaccore. dll_ não foi encontrado no mesmo diretório que o CoreCLR. dll de destino.</span><span class="sxs-lookup"><span data-stu-id="7565c-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="7565c-114">MSCorDbi. dll ou mscordaccore. dll não é a mesma versão que o CoreCLR. dll de destino.</span><span class="sxs-lookup"><span data-stu-id="7565c-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="7565c-115">`E_FAIL`(ou outros `E_` códigos de retorno) </span><span class="sxs-lookup"><span data-stu-id="7565c-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="7565c-116">Não é possível retornar uma [interface ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7565c-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7565c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="7565c-117">Remarks</span></span>

 <span data-ttu-id="7565c-118">A interface retornada fornece os recursos para anexar a um CLR em um processo de destino e depurar o código gerenciado que o CLR está executando.</span><span class="sxs-lookup"><span data-stu-id="7565c-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7565c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7565c-119">Requirements</span></span>

 <span data-ttu-id="7565c-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7565c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7565c-121">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="7565c-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7565c-122">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="7565c-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7565c-123">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7565c-123">**.NET Framework Versions:** 3.5 SP1</span></span>
