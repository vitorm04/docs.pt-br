---
title: Método ExportTypeForwarder
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bdf9fb50fe06141df6f3818c784588b9e2138af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789916"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="eddbe-102">Método ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="eddbe-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="eddbe-103">Adiciona um encaminhador de tipo para a tabela de tipo do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="eddbe-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eddbe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eddbe-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eddbe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eddbe-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="eddbe-106">Referência ao assembly ao qual se refere o encaminhador de tipo.</span><span class="sxs-lookup"><span data-stu-id="eddbe-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="eddbe-107">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="eddbe-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eddbe-108">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="eddbe-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="eddbe-109">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="eddbe-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="eddbe-110">Recebe o token do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="eddbe-110">Receives the token of the exported type.</span></span> <span data-ttu-id="eddbe-111">Isso é necessário apenas para emitir tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="eddbe-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eddbe-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="eddbe-112">Return Value</span></span>  
 <span data-ttu-id="eddbe-113">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="eddbe-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eddbe-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eddbe-114">Requirements</span></span>  
 <span data-ttu-id="eddbe-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="eddbe-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eddbe-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eddbe-116">See also</span></span>

- [<span data-ttu-id="eddbe-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="eddbe-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="eddbe-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="eddbe-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="eddbe-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="eddbe-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
