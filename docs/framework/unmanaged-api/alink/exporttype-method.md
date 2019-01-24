---
title: Método ExportType
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ce6478f0331c590a2384a4e7e9b5621c050715d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623632"
---
# <a name="exporttype-method"></a><span data-ttu-id="714b3-102">Método ExportType</span><span class="sxs-lookup"><span data-stu-id="714b3-102">ExportType Method</span></span>
<span data-ttu-id="714b3-103">Especifica que um tipo é exportável.</span><span class="sxs-lookup"><span data-stu-id="714b3-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="714b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="714b3-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="714b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="714b3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="714b3-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="714b3-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="714b3-107">Assembly ou token de ID de arquivo que define o tipo exportável.</span><span class="sxs-lookup"><span data-stu-id="714b3-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="714b3-108">Token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="714b3-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="714b3-109">Nome de tipo totalmente qualificado a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="714b3-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="714b3-110">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="714b3-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="714b3-111">Esse parâmetro pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="714b3-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="714b3-112">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="714b3-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="714b3-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="714b3-113">Return Value</span></span>  
 <span data-ttu-id="714b3-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="714b3-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="714b3-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="714b3-115">Requirements</span></span>  
 <span data-ttu-id="714b3-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="714b3-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714b3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="714b3-117">See also</span></span>
- [<span data-ttu-id="714b3-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="714b3-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="714b3-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="714b3-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="714b3-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="714b3-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
