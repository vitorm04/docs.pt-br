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
ms.openlocfilehash: 1cd1c077a8f2a5fe3b2b46c2e1da2e92b5a797a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402051"
---
# <a name="emitassembly-method"></a><span data-ttu-id="d62b1-102">Método EmitAssembly</span><span class="sxs-lookup"><span data-stu-id="d62b1-102">EmitAssembly Method</span></span>
<span data-ttu-id="d62b1-103">Cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="d62b1-103">Creates the assembly.</span></span> <span data-ttu-id="d62b1-104">Chame este método depois que todos os outros arquivos são fechados, exceto o arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="d62b1-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="d62b1-105">Não chame este método durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="d62b1-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d62b1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d62b1-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d62b1-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d62b1-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d62b1-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d62b1-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d62b1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d62b1-109">Return Value</span></span>  
 <span data-ttu-id="d62b1-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d62b1-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d62b1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d62b1-111">Requirements</span></span>  
 <span data-ttu-id="d62b1-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="d62b1-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62b1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d62b1-113">See Also</span></span>  
 [<span data-ttu-id="d62b1-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d62b1-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d62b1-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d62b1-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d62b1-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d62b1-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
