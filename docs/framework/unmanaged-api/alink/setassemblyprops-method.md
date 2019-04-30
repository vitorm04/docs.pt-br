---
title: Método SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 589bd7b2132693c89dc10ae1a5c8d0bf52ed481e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949078"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="aa682-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="aa682-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="aa682-103">Atribui a propriedades de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="aa682-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa682-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa682-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa682-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa682-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="aa682-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="aa682-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="aa682-107">Arquivo que define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="aa682-107">File that defines the property.</span></span> <span data-ttu-id="aa682-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="aa682-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="aa682-109">Indica a opção de modificar.</span><span class="sxs-lookup"><span data-stu-id="aa682-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="aa682-110">Novo valor da opção.</span><span class="sxs-lookup"><span data-stu-id="aa682-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa682-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="aa682-111">Return Value</span></span>  
 <span data-ttu-id="aa682-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="aa682-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa682-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa682-113">Requirements</span></span>  
 <span data-ttu-id="aa682-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="aa682-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa682-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa682-115">See also</span></span>

- [<span data-ttu-id="aa682-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="aa682-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="aa682-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="aa682-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="aa682-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="aa682-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
