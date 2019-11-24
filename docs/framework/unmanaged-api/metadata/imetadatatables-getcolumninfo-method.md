---
title: Método IMetaDataTables::GetColumnInfo
ms.date: 10/10/2019
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
ms.openlocfilehash: 854d3ad28cc00c03e903b9e1d2ce3863e3ceef17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436099"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="6a5f9-102">Método IMetaDataTables::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="6a5f9-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="6a5f9-103">Gets data about the specified column in the specified table.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a5f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a5f9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a5f9-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="6a5f9-106">[in] The index of the desired table.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="6a5f9-107">[in] The index of the desired column.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="6a5f9-108">[out] A pointer to the offset of the column in the row.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="6a5f9-109">[out] A pointer to the size, in bytes, of the column.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="6a5f9-110">[out] A pointer to the type of the values in the column.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6a5f9-111">[out] A pointer to a pointer to the column name.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="6a5f9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a5f9-112">Remarks</span></span>

<span data-ttu-id="6a5f9-113">The returned column type falls within a range of values:</span><span class="sxs-lookup"><span data-stu-id="6a5f9-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="6a5f9-114">pType</span><span class="sxs-lookup"><span data-stu-id="6a5f9-114">pType</span></span>                    | <span data-ttu-id="6a5f9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a5f9-115">Description</span></span>   | <span data-ttu-id="6a5f9-116">Helper function</span><span class="sxs-lookup"><span data-stu-id="6a5f9-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="6a5f9-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="6a5f9-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="6a5f9-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-118">(0..63)</span></span>   | <span data-ttu-id="6a5f9-119">Rid</span><span class="sxs-lookup"><span data-stu-id="6a5f9-119">Rid</span></span>           | <span data-ttu-id="6a5f9-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-120">**IsRidType**</span></span><br><span data-ttu-id="6a5f9-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="6a5f9-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="6a5f9-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="6a5f9-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-123">(64..95)</span></span> | <span data-ttu-id="6a5f9-124">Coded token</span><span class="sxs-lookup"><span data-stu-id="6a5f9-124">Coded token</span></span> | <span data-ttu-id="6a5f9-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="6a5f9-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="6a5f9-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="6a5f9-128">Int16</span><span class="sxs-lookup"><span data-stu-id="6a5f9-128">Int16</span></span>         | <span data-ttu-id="6a5f9-129">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6a5f9-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="6a5f9-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="6a5f9-131">UInt16</span></span>        | <span data-ttu-id="6a5f9-132">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6a5f9-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-133">`iLONG` (98)</span></span>             | <span data-ttu-id="6a5f9-134">Int32</span><span class="sxs-lookup"><span data-stu-id="6a5f9-134">Int32</span></span>         | <span data-ttu-id="6a5f9-135">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6a5f9-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-136">`iULONG` (99)</span></span>            | <span data-ttu-id="6a5f9-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="6a5f9-137">UInt32</span></span>        | <span data-ttu-id="6a5f9-138">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6a5f9-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="6a5f9-140">Byte</span><span class="sxs-lookup"><span data-stu-id="6a5f9-140">Byte</span></span>          | <span data-ttu-id="6a5f9-141">**IsFixedType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="6a5f9-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="6a5f9-143">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6a5f9-143">String</span></span>        | <span data-ttu-id="6a5f9-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="6a5f9-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-145">`iGUID` (102)</span></span>            | <span data-ttu-id="6a5f9-146">GUID</span><span class="sxs-lookup"><span data-stu-id="6a5f9-146">Guid</span></span>          | <span data-ttu-id="6a5f9-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="6a5f9-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="6a5f9-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="6a5f9-149">Blob</span><span class="sxs-lookup"><span data-stu-id="6a5f9-149">Blob</span></span>          | <span data-ttu-id="6a5f9-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="6a5f9-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span><span class="sxs-lookup"><span data-stu-id="6a5f9-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="6a5f9-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="6a5f9-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="6a5f9-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="6a5f9-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a5f9-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span><span class="sxs-lookup"><span data-stu-id="6a5f9-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a5f9-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a5f9-156">Requirements</span></span>  
 <span data-ttu-id="6a5f9-157">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5f9-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5f9-158">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a5f9-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a5f9-159">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a5f9-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a5f9-160">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5f9-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5f9-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a5f9-161">See also</span></span>

- [<span data-ttu-id="6a5f9-162">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="6a5f9-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="6a5f9-163">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="6a5f9-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
