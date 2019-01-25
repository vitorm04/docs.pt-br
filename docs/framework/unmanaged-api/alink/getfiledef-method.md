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
ms.openlocfilehash: c6a8a9aedc5c2b09c6e6f6014142bce44f3a8297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668594"
---
# <a name="getfiledef-method"></a><span data-ttu-id="f1e6f-102">Método GetFileDef</span><span class="sxs-lookup"><span data-stu-id="f1e6f-102">GetFileDef Method</span></span>
<span data-ttu-id="f1e6f-103">Recupera o token FileDef real usado nos metadados (em vez do token atribuído pelo ALink).</span><span class="sxs-lookup"><span data-stu-id="f1e6f-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1e6f-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1e6f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1e6f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f1e6f-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f1e6f-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="f1e6f-107">Token do arquivo adicionado, conforme recuperados do método AddFile ou método AddImport.</span><span class="sxs-lookup"><span data-stu-id="f1e6f-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="f1e6f-108">Recebe o token FileDef.</span><span class="sxs-lookup"><span data-stu-id="f1e6f-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1e6f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1e6f-109">Return Value</span></span>  
 <span data-ttu-id="f1e6f-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="f1e6f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e6f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1e6f-111">Requirements</span></span>  
 <span data-ttu-id="f1e6f-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f1e6f-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e6f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1e6f-113">See also</span></span>
- [<span data-ttu-id="f1e6f-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f1e6f-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f1e6f-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f1e6f-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f1e6f-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f1e6f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
