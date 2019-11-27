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
ms.openlocfilehash: 6bbe5db75ded15f32a6ff3564e1116d40a745a65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446526"
---
# <a name="emitassembly-method"></a><span data-ttu-id="73f7e-102">Método EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="73f7e-102">EmitAssembly Method</span></span>
<span data-ttu-id="73f7e-103">Cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="73f7e-103">Creates the assembly.</span></span> <span data-ttu-id="73f7e-104">Chame esse método depois que todos os outros arquivos forem fechados, exceto o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="73f7e-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="73f7e-105">Não chame esse método ao produzir módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="73f7e-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f7e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73f7e-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="73f7e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73f7e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="73f7e-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="73f7e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73f7e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="73f7e-109">Return Value</span></span>  
 <span data-ttu-id="73f7e-110">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="73f7e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f7e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73f7e-111">Requirements</span></span>  
 <span data-ttu-id="73f7e-112">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="73f7e-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f7e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f7e-113">See also</span></span>

- [<span data-ttu-id="73f7e-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="73f7e-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="73f7e-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="73f7e-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="73f7e-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="73f7e-116">ALink API</span></span>](index.md)
