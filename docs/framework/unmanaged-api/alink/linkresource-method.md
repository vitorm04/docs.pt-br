---
title: Método LinkResource
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763b7a776007c2ce8dac42c6a5f7f00f6eb58a10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776951"
---
# <a name="linkresource-method"></a><span data-ttu-id="c17bf-102">Método LinkResource</span><span class="sxs-lookup"><span data-stu-id="c17bf-102">LinkResource Method</span></span>
<span data-ttu-id="c17bf-103">Links em um recurso.</span><span class="sxs-lookup"><span data-stu-id="c17bf-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c17bf-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c17bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c17bf-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c17bf-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="c17bf-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="c17bf-107">Nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c17bf-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="c17bf-108">Novo nome de arquivo opcional.</span><span class="sxs-lookup"><span data-stu-id="c17bf-108">Optional new file name.</span></span> <span data-ttu-id="c17bf-109">Se não for NULL, `pszFileName` será copiado para pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="c17bf-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="c17bf-110">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="c17bf-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c17bf-111">Sinalizadores de acessibilidade, `mrPublic` como `mrPrivate`e.</span><span class="sxs-lookup"><span data-stu-id="c17bf-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="c17bf-112">Esse parâmetro pode ser passado para o [método DefineManifestResource](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="c17bf-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c17bf-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c17bf-113">Return Value</span></span>  
 <span data-ttu-id="c17bf-114">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="c17bf-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17bf-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c17bf-115">Requirements</span></span>  
 <span data-ttu-id="c17bf-116">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c17bf-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17bf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c17bf-117">See also</span></span>

- [<span data-ttu-id="c17bf-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c17bf-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c17bf-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c17bf-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c17bf-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c17bf-120">ALink API</span></span>](index.md)
