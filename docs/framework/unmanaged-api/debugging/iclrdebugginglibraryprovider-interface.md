---
title: Interface ICLRDebuggingLibraryProvider
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: 77c2011ce677d1bd2823d47740782f48151b408a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860285"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="48263-102">Interface ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="48263-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="48263-103">Inclui o método de [método ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) , que obtém uma interface de retorno de chamada do provedor de biblioteca que permite que Common Language Runtime bibliotecas de depuração específicas à versão sejam localizadas e carregadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="48263-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48263-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="48263-104">Methods</span></span>  
  
|<span data-ttu-id="48263-105">Método</span><span class="sxs-lookup"><span data-stu-id="48263-105">Method</span></span>|<span data-ttu-id="48263-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="48263-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48263-107">Método ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="48263-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="48263-108">Permite que o depurador forneça um identificador para um módulo que pode ser usado para carregar uma biblioteca de depuração.</span><span class="sxs-lookup"><span data-stu-id="48263-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48263-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48263-109">Requirements</span></span>  
 <span data-ttu-id="48263-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48263-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48263-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48263-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48263-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48263-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48263-113">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48263-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48263-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="48263-114">See also</span></span>

- [<span data-ttu-id="48263-115">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="48263-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="48263-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="48263-116">Debugging</span></span>](index.md)
