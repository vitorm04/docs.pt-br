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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789929"
---
# <a name="exporttype-method"></a><span data-ttu-id="48f1b-102">Método ExportType</span><span class="sxs-lookup"><span data-stu-id="48f1b-102">ExportType Method</span></span>
<span data-ttu-id="48f1b-103">Especifica que um tipo é exportável.</span><span class="sxs-lookup"><span data-stu-id="48f1b-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48f1b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="48f1b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48f1b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="48f1b-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="48f1b-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="48f1b-107">Assembly ou token de ID de arquivo que define o tipo exportável.</span><span class="sxs-lookup"><span data-stu-id="48f1b-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="48f1b-108">Token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="48f1b-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="48f1b-109">Nome de tipo totalmente qualificado a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="48f1b-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="48f1b-110">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="48f1b-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="48f1b-111">Esse parâmetro pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="48f1b-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="48f1b-112">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="48f1b-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48f1b-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="48f1b-113">Return Value</span></span>  
 <span data-ttu-id="48f1b-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="48f1b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f1b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48f1b-115">Requirements</span></span>  
 <span data-ttu-id="48f1b-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="48f1b-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f1b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48f1b-117">See also</span></span>

- [<span data-ttu-id="48f1b-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="48f1b-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="48f1b-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="48f1b-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="48f1b-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="48f1b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
