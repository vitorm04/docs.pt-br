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
ms.openlocfilehash: 5db205993bc1a0665dc0003948ce805813251f48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787456"
---
# <a name="getfiledef-method"></a><span data-ttu-id="4a78c-102">Método GetFileDef</span><span class="sxs-lookup"><span data-stu-id="4a78c-102">GetFileDef Method</span></span>
<span data-ttu-id="4a78c-103">Recupera o token FileDef real usado nos metadados (em oposição ao token atribuído pelo ALink).</span><span class="sxs-lookup"><span data-stu-id="4a78c-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a78c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a78c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a78c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a78c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4a78c-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="4a78c-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="4a78c-107">Token do arquivo adicionado como recuperado do método AddFile ou do método AddImport.</span><span class="sxs-lookup"><span data-stu-id="4a78c-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="4a78c-108">Recebe o token FileDef.</span><span class="sxs-lookup"><span data-stu-id="4a78c-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a78c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4a78c-109">Return Value</span></span>  
 <span data-ttu-id="4a78c-110">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="4a78c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a78c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a78c-111">Requirements</span></span>  
 <span data-ttu-id="4a78c-112">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="4a78c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a78c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a78c-113">See also</span></span>

- [<span data-ttu-id="4a78c-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="4a78c-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4a78c-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="4a78c-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4a78c-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="4a78c-116">ALink API</span></span>](index.md)
