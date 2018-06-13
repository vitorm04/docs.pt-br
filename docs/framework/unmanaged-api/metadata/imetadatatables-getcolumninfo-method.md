---
title: Método IMetaDataTables::GetColumnInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79f08109f1ad267c4898cc0789859b55f534d1b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448075"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="ef71e-102">Método IMetaDataTables::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="ef71e-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="ef71e-103">Obtém dados sobre a coluna especificada na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="ef71e-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef71e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef71e-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef71e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef71e-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ef71e-106">[in] O índice da tabela desejada.</span><span class="sxs-lookup"><span data-stu-id="ef71e-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="ef71e-107">[in] O índice da coluna desejada.</span><span class="sxs-lookup"><span data-stu-id="ef71e-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="ef71e-108">[out] Um ponteiro para o deslocamento da coluna na linha.</span><span class="sxs-lookup"><span data-stu-id="ef71e-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="ef71e-109">[out] Um ponteiro para o tamanho, em bytes, da coluna.</span><span class="sxs-lookup"><span data-stu-id="ef71e-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="ef71e-110">[out] Um ponteiro para o tipo de valores na coluna.</span><span class="sxs-lookup"><span data-stu-id="ef71e-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ef71e-111">[out] Um ponteiro para um ponteiro para o nome da coluna.</span><span class="sxs-lookup"><span data-stu-id="ef71e-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef71e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef71e-112">Requirements</span></span>  
 <span data-ttu-id="ef71e-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef71e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef71e-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef71e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef71e-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ef71e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef71e-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef71e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef71e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef71e-117">See Also</span></span>  
 [<span data-ttu-id="ef71e-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ef71e-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ef71e-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ef71e-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
