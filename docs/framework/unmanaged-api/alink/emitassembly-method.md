---
title: Método EmitAssembly
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787587"
---
# <a name="emitassembly-method"></a><span data-ttu-id="58968-102">Método EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="58968-102">EmitAssembly Method</span></span>
<span data-ttu-id="58968-103">Cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="58968-103">Creates the assembly.</span></span> <span data-ttu-id="58968-104">Chame esse método depois que todos os outros arquivos forem fechados, exceto o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="58968-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="58968-105">Não chame esse método ao produzir módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="58968-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58968-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58968-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="58968-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58968-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="58968-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="58968-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58968-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="58968-109">Return Value</span></span>  
 <span data-ttu-id="58968-110">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="58968-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58968-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58968-111">Requirements</span></span>  
 <span data-ttu-id="58968-112">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="58968-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58968-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58968-113">See also</span></span>

- [<span data-ttu-id="58968-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="58968-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="58968-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="58968-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="58968-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="58968-116">ALink API</span></span>](index.md)
