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
ms.openlocfilehash: b1cdcfcaf29cc2b0ec6da1108e0ecd91710db36c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487298"
---
# <a name="emitassembly-method"></a><span data-ttu-id="fdd06-102">Método EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="fdd06-102">EmitAssembly Method</span></span>
<span data-ttu-id="fdd06-103">Cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="fdd06-103">Creates the assembly.</span></span> <span data-ttu-id="fdd06-104">Chame esse método depois que todos os outros arquivos são fechados, exceto para o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="fdd06-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="fdd06-105">Não chame este método durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="fdd06-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd06-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdd06-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdd06-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fdd06-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fdd06-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="fdd06-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdd06-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fdd06-109">Return Value</span></span>  
 <span data-ttu-id="fdd06-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="fdd06-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd06-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdd06-111">Requirements</span></span>  
 <span data-ttu-id="fdd06-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="fdd06-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd06-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdd06-113">See also</span></span>
- [<span data-ttu-id="fdd06-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="fdd06-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fdd06-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="fdd06-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="fdd06-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="fdd06-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
