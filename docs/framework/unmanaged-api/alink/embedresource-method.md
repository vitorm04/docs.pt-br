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
ms.openlocfilehash: ef7d6272c04c3edab8ef652bcb2759861ff2b982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129565"
---
# <a name="embedresource-method"></a><span data-ttu-id="ad120-102">Método EmbedResource</span><span class="sxs-lookup"><span data-stu-id="ad120-102">EmbedResource Method</span></span>
<span data-ttu-id="ad120-103">Declara um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="ad120-103">Declares an embedded resource.</span></span> <span data-ttu-id="ad120-104">Esse método insere, na verdade, o recurso.</span><span class="sxs-lookup"><span data-stu-id="ad120-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad120-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad120-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad120-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad120-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ad120-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="ad120-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ad120-108">Assembly ou token de ID de arquivo que contém o recurso.</span><span class="sxs-lookup"><span data-stu-id="ad120-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="ad120-109">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="ad120-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ad120-110">Deslocamento do recurso de RVA.</span><span class="sxs-lookup"><span data-stu-id="ad120-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ad120-111">Acessibilidade, como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="ad120-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="ad120-112">Esses sinalizadores podem ser passados para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ad120-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad120-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ad120-113">Return Value</span></span>  
 <span data-ttu-id="ad120-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="ad120-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad120-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad120-115">Requirements</span></span>  
 <span data-ttu-id="ad120-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="ad120-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad120-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad120-117">See also</span></span>

- [<span data-ttu-id="ad120-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ad120-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ad120-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ad120-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ad120-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ad120-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
