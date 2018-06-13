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
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405392"
---
# <a name="embedresource-method"></a><span data-ttu-id="7ae8a-102">Método EmbedResource</span><span class="sxs-lookup"><span data-stu-id="7ae8a-102">EmbedResource Method</span></span>
<span data-ttu-id="7ae8a-103">Declara um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-103">Declares an embedded resource.</span></span> <span data-ttu-id="7ae8a-104">Esse método não insere, na verdade, o recurso.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae8a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ae8a-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ae8a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ae8a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7ae8a-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7ae8a-108">ID de token ou assembly de arquivo que contém o recurso do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="7ae8a-109">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="7ae8a-110">Deslocamento do recurso do RVA.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7ae8a-111">Acessibilidade como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="7ae8a-112">Esses sinalizadores podem ser passados para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ae8a-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ae8a-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7ae8a-113">Return Value</span></span>  
 <span data-ttu-id="7ae8a-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae8a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ae8a-115">Requirements</span></span>  
 <span data-ttu-id="7ae8a-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="7ae8a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae8a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ae8a-117">See Also</span></span>  
 [<span data-ttu-id="7ae8a-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="7ae8a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7ae8a-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="7ae8a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7ae8a-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="7ae8a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
