---
title: Método ExportNestedTypeForwarder
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb8112d6d2b5c2cbb257db2f20ff4be5a84e827b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787480"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="2354a-102">Método ExportNestedTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="2354a-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="2354a-103">Adiciona um encaminhador de tipo para um tipo aninhado à tabela de tipos do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="2354a-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2354a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2354a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2354a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2354a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2354a-106">ID do assembly do qual exportar.</span><span class="sxs-lookup"><span data-stu-id="2354a-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2354a-107">Token do arquivo ou ID do assembly do arquivo que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="2354a-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="2354a-108">Token para o tipo.</span><span class="sxs-lookup"><span data-stu-id="2354a-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="2354a-109">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="2354a-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="2354a-110">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="2354a-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2354a-111">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="2354a-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="2354a-112">Recebe o token do tipo de exportação.</span><span class="sxs-lookup"><span data-stu-id="2354a-112">Receives token of export type.</span></span> <span data-ttu-id="2354a-113">Isso é necessário apenas para emitir tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="2354a-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2354a-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2354a-114">Return Value</span></span>  
 <span data-ttu-id="2354a-115">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="2354a-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2354a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2354a-116">Requirements</span></span>  
 <span data-ttu-id="2354a-117">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="2354a-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2354a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2354a-118">See also</span></span>

- [<span data-ttu-id="2354a-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="2354a-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2354a-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="2354a-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2354a-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="2354a-121">ALink API</span></span>](index.md)
