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
ms.openlocfilehash: 95ff27143453e7772b4a463fa66ca039bbb715fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226911"
---
# <a name="exporttype-method"></a><span data-ttu-id="713e0-102">Método ExportType</span><span class="sxs-lookup"><span data-stu-id="713e0-102">ExportType Method</span></span>
<span data-ttu-id="713e0-103">Especifica que um tipo é exportável.</span><span class="sxs-lookup"><span data-stu-id="713e0-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="713e0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="713e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="713e0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="713e0-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="713e0-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="713e0-107">Assembly ou token de ID de arquivo que define o tipo exportável.</span><span class="sxs-lookup"><span data-stu-id="713e0-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="713e0-108">Token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="713e0-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="713e0-109">Nome de tipo totalmente qualificado a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="713e0-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="713e0-110">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="713e0-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="713e0-111">Esse parâmetro pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="713e0-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="713e0-112">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="713e0-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="713e0-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="713e0-113">Return Value</span></span>  
 <span data-ttu-id="713e0-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="713e0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713e0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="713e0-115">Requirements</span></span>  
 <span data-ttu-id="713e0-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="713e0-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713e0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="713e0-117">See also</span></span>

- [<span data-ttu-id="713e0-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="713e0-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="713e0-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="713e0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="713e0-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="713e0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
