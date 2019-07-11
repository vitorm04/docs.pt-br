---
title: Método IMetaDataTables::GetNumTables
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb26a96c46b01a2981afba0ac6b405c0b50f6d9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781428"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="889ef-102">Método IMetaDataTables::GetNumTables</span><span class="sxs-lookup"><span data-stu-id="889ef-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="889ef-103">Obtém o número de tabelas no escopo atual `IMetaDataTables` instância.</span><span class="sxs-lookup"><span data-stu-id="889ef-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="889ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="889ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="889ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="889ef-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="889ef-106">[out] Um ponteiro para o número de tabelas no escopo atual da instância.</span><span class="sxs-lookup"><span data-stu-id="889ef-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="889ef-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="889ef-107">Requirements</span></span>  
 <span data-ttu-id="889ef-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="889ef-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="889ef-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="889ef-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="889ef-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="889ef-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="889ef-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889ef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889ef-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="889ef-112">See also</span></span>

- [<span data-ttu-id="889ef-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="889ef-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="889ef-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="889ef-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
