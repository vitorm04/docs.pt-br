---
title: Método EmbedResource
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f6140e5f85a7ee21773c96a5abdccadaddab92e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777452"
---
# <a name="embedresource-method"></a><span data-ttu-id="eb2df-102">Método EmbedResource</span><span class="sxs-lookup"><span data-stu-id="eb2df-102">EmbedResource Method</span></span>
<span data-ttu-id="eb2df-103">Declara um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="eb2df-103">Declares an embedded resource.</span></span> <span data-ttu-id="eb2df-104">Esse método não insere o recurso de fato.</span><span class="sxs-lookup"><span data-stu-id="eb2df-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2df-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb2df-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2df-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb2df-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eb2df-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="eb2df-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="eb2df-108">Token do arquivo ou ID do assembly do arquivo que contém o recurso.</span><span class="sxs-lookup"><span data-stu-id="eb2df-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="eb2df-109">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="eb2df-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="eb2df-110">Deslocamento do recurso de RVA.</span><span class="sxs-lookup"><span data-stu-id="eb2df-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eb2df-111">Sinalizadores de acessibilidade, `mrPublic` como `mrPrivate`e.</span><span class="sxs-lookup"><span data-stu-id="eb2df-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="eb2df-112">Esses sinalizadores podem ser passados para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb2df-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb2df-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="eb2df-113">Return Value</span></span>  
 <span data-ttu-id="eb2df-114">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="eb2df-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2df-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb2df-115">Requirements</span></span>  
 <span data-ttu-id="eb2df-116">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="eb2df-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2df-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb2df-117">See also</span></span>

- [<span data-ttu-id="eb2df-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="eb2df-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="eb2df-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="eb2df-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="eb2df-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="eb2df-120">ALink API</span></span>](index.md)
