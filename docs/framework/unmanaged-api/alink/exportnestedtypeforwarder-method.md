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
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404086"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="91874-102">Método ExportNestedTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="91874-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="91874-103">Adiciona um encaminhador de tipo para um tipo aninhado para o tipo de tabela do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="91874-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91874-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91874-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="91874-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91874-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="91874-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="91874-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="91874-107">Arquivo ID do arquivo que define o tipo de token ou assembly.</span><span class="sxs-lookup"><span data-stu-id="91874-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="91874-108">Token para o tipo.</span><span class="sxs-lookup"><span data-stu-id="91874-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="91874-109">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="91874-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="91874-110">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="91874-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="91874-111">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="91874-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="91874-112">Recebe o token do tipo de exportação.</span><span class="sxs-lookup"><span data-stu-id="91874-112">Receives token of export type.</span></span> <span data-ttu-id="91874-113">Isso é necessário apenas para a emissão de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="91874-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91874-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91874-114">Return Value</span></span>  
 <span data-ttu-id="91874-115">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="91874-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91874-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91874-116">Requirements</span></span>  
 <span data-ttu-id="91874-117">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="91874-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91874-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91874-118">See Also</span></span>  
 [<span data-ttu-id="91874-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="91874-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="91874-120">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="91874-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="91874-121">API do ALink</span><span class="sxs-lookup"><span data-stu-id="91874-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
