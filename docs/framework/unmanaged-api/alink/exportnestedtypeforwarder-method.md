---
title: "Método ExportNestedTypeForwarder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41c0984e4439b89ddee2b55bbca7a098075d6bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="da4c0-102">Método ExportNestedTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="da4c0-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="da4c0-103">Adiciona um encaminhador de tipo para um tipo aninhado para o tipo de tabela do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="da4c0-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da4c0-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="da4c0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da4c0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="da4c0-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="da4c0-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="da4c0-107">Arquivo ID do arquivo que define o tipo de token ou assembly.</span><span class="sxs-lookup"><span data-stu-id="da4c0-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="da4c0-108">Token para o tipo.</span><span class="sxs-lookup"><span data-stu-id="da4c0-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="da4c0-109">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="da4c0-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="da4c0-110">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="da4c0-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="da4c0-111">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="da4c0-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="da4c0-112">Recebe o token do tipo de exportação.</span><span class="sxs-lookup"><span data-stu-id="da4c0-112">Receives token of export type.</span></span> <span data-ttu-id="da4c0-113">Isso é necessário apenas para a emissão de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="da4c0-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da4c0-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="da4c0-114">Return Value</span></span>  
 <span data-ttu-id="da4c0-115">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="da4c0-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4c0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da4c0-116">Requirements</span></span>  
 <span data-ttu-id="da4c0-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="da4c0-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4c0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da4c0-118">See Also</span></span>  
 [<span data-ttu-id="da4c0-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="da4c0-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="da4c0-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="da4c0-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="da4c0-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="da4c0-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
