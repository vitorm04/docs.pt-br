---
title: Método PreCloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787227"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="16b0e-102">Método PreCloseAssembly</span><span class="sxs-lookup"><span data-stu-id="16b0e-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="16b0e-103">Fecha o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="16b0e-103">Closes the assembly file.</span></span> <span data-ttu-id="16b0e-104">Chame esse método depois de fechar todos os outros arquivos, mas antes de fechar o arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="16b0e-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="16b0e-105">Não chame esse método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="16b0e-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b0e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16b0e-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="16b0e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16b0e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="16b0e-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="16b0e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16b0e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="16b0e-109">Return Value</span></span>  
 <span data-ttu-id="16b0e-110">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="16b0e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16b0e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16b0e-111">Requirements</span></span>  
 <span data-ttu-id="16b0e-112">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="16b0e-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b0e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16b0e-113">See also</span></span>

- [<span data-ttu-id="16b0e-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="16b0e-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="16b0e-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="16b0e-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="16b0e-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="16b0e-116">ALink API</span></span>](index.md)
