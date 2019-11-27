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
ms.openlocfilehash: 6a561205602920123176bd421ca2ef1b601166c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426056"
---
# <a name="getfiledef-method"></a><span data-ttu-id="2ed60-102">Método GetFileDef</span><span class="sxs-lookup"><span data-stu-id="2ed60-102">GetFileDef Method</span></span>
<span data-ttu-id="2ed60-103">Recupera o token FileDef real usado nos metadados (em oposição ao token atribuído pelo ALink).</span><span class="sxs-lookup"><span data-stu-id="2ed60-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed60-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ed60-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ed60-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ed60-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2ed60-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="2ed60-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="2ed60-107">Token do arquivo adicionado como recuperado do método AddFile ou do método AddImport.</span><span class="sxs-lookup"><span data-stu-id="2ed60-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="2ed60-108">Recebe o token FileDef.</span><span class="sxs-lookup"><span data-stu-id="2ed60-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ed60-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2ed60-109">Return Value</span></span>  
 <span data-ttu-id="2ed60-110">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="2ed60-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ed60-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ed60-111">Requirements</span></span>  
 <span data-ttu-id="2ed60-112">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="2ed60-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed60-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ed60-113">See also</span></span>

- [<span data-ttu-id="2ed60-114">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="2ed60-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2ed60-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="2ed60-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2ed60-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="2ed60-116">ALink API</span></span>](index.md)
