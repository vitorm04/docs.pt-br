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
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438574"
---
# <a name="exporttype-method"></a><span data-ttu-id="0f73c-102">Método ExportType</span><span class="sxs-lookup"><span data-stu-id="0f73c-102">ExportType Method</span></span>
<span data-ttu-id="0f73c-103">Especifica que um tipo é exportável.</span><span class="sxs-lookup"><span data-stu-id="0f73c-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f73c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f73c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f73c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f73c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0f73c-106">ID do assembly do qual exportar.</span><span class="sxs-lookup"><span data-stu-id="0f73c-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0f73c-107">Token do arquivo ou ID do assembly do arquivo que define o tipo exportável.</span><span class="sxs-lookup"><span data-stu-id="0f73c-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="0f73c-108">Token do tipo a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="0f73c-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="0f73c-109">Nome de tipo totalmente qualificado a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="0f73c-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0f73c-110">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="0f73c-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="0f73c-111">Esse parâmetro pode ser passado para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="0f73c-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="0f73c-112">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="0f73c-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f73c-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0f73c-113">Return Value</span></span>  
 <span data-ttu-id="0f73c-114">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="0f73c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f73c-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0f73c-115">Requirements</span></span>  
 <span data-ttu-id="0f73c-116">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="0f73c-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f73c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f73c-117">See also</span></span>

- [<span data-ttu-id="0f73c-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="0f73c-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0f73c-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="0f73c-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0f73c-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="0f73c-120">ALink API</span></span>](index.md)
