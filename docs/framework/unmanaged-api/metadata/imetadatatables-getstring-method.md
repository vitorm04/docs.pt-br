---
title: "Método IMetaDataTables::GetString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c2c0df58d1de7cc7c1eedfdea6c0e698cbd9cb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="3aebe-102">Método IMetaDataTables::GetString</span><span class="sxs-lookup"><span data-stu-id="3aebe-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="3aebe-103">Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo de referência atual.</span><span class="sxs-lookup"><span data-stu-id="3aebe-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aebe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3aebe-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3aebe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3aebe-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="3aebe-106">[in] O índice no qual começar a procurar o próximo valor.</span><span class="sxs-lookup"><span data-stu-id="3aebe-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="3aebe-107">[out] Um ponteiro para um ponteiro para o valor de cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="3aebe-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aebe-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3aebe-108">Requirements</span></span>  
 <span data-ttu-id="3aebe-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aebe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aebe-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3aebe-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3aebe-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3aebe-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aebe-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aebe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aebe-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aebe-113">See Also</span></span>  
 [<span data-ttu-id="3aebe-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="3aebe-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3aebe-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="3aebe-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
