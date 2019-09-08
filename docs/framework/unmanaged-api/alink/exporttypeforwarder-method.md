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
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787501"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="c9092-102">Método ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="c9092-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="c9092-103">Adiciona um encaminhador de tipo à tabela de tipos do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="c9092-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9092-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9092-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9092-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9092-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="c9092-106">Referência ao assembly ao qual o encaminhador de tipo se refere.</span><span class="sxs-lookup"><span data-stu-id="c9092-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c9092-107">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="c9092-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c9092-108">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="c9092-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="c9092-109">Esse valor pode ser passado para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="c9092-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="c9092-110">Recebe o token do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c9092-110">Receives the token of the exported type.</span></span> <span data-ttu-id="c9092-111">Isso é necessário apenas para emitir tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="c9092-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9092-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9092-112">Return Value</span></span>  
 <span data-ttu-id="c9092-113">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="c9092-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9092-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9092-114">Requirements</span></span>  
 <span data-ttu-id="c9092-115">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="c9092-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9092-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9092-116">See also</span></span>

- [<span data-ttu-id="c9092-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c9092-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c9092-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c9092-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c9092-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c9092-119">ALink API</span></span>](index.md)
