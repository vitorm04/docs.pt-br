---
title: Método GetFileDef
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7cc7b83f7bf1657195778ea38944b2354b09c38
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471336"
---
# <a name="getfiledef-method"></a><span data-ttu-id="493e2-102">Método GetFileDef</span><span class="sxs-lookup"><span data-stu-id="493e2-102">GetFileDef Method</span></span>
<span data-ttu-id="493e2-103">Recupera o token FileDef real usado nos metadados (em vez do token atribuído pelo ALink).</span><span class="sxs-lookup"><span data-stu-id="493e2-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="493e2-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="493e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="493e2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="493e2-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="493e2-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="493e2-107">Token do arquivo adicionado, conforme recuperados do método AddFile ou método AddImport.</span><span class="sxs-lookup"><span data-stu-id="493e2-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="493e2-108">Recebe o token FileDef.</span><span class="sxs-lookup"><span data-stu-id="493e2-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="493e2-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="493e2-109">Return Value</span></span>  
 <span data-ttu-id="493e2-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="493e2-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493e2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="493e2-111">Requirements</span></span>  
 <span data-ttu-id="493e2-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="493e2-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493e2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="493e2-113">See also</span></span>
- [<span data-ttu-id="493e2-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="493e2-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="493e2-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="493e2-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="493e2-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="493e2-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
