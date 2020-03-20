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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177128"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="086ca-102">Método IMetaDataTables::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="086ca-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="086ca-103">Obtém dados sobre a coluna especificada na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="086ca-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="086ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="086ca-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="086ca-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="086ca-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="086ca-106">[em] O índice da tabela desejada.</span><span class="sxs-lookup"><span data-stu-id="086ca-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="086ca-107">[em] O índice da coluna desejada.</span><span class="sxs-lookup"><span data-stu-id="086ca-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="086ca-108">[fora] Um ponteiro para o deslocamento da coluna na linha.</span><span class="sxs-lookup"><span data-stu-id="086ca-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="086ca-109">[fora] Um ponteiro para o tamanho, em bytes, da coluna.</span><span class="sxs-lookup"><span data-stu-id="086ca-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="086ca-110">[fora] Um ponteiro para o tipo de valores na coluna.</span><span class="sxs-lookup"><span data-stu-id="086ca-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="086ca-111">[fora] Um ponteiro para um ponteiro para o nome da coluna.</span><span class="sxs-lookup"><span data-stu-id="086ca-111">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="086ca-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="086ca-112">Remarks</span></span>

<span data-ttu-id="086ca-113">O tipo de coluna retornada está dentro de uma variedade de valores:</span><span class="sxs-lookup"><span data-stu-id="086ca-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="086ca-114">Ptype</span><span class="sxs-lookup"><span data-stu-id="086ca-114">pType</span></span>                    | <span data-ttu-id="086ca-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="086ca-115">Description</span></span>   | <span data-ttu-id="086ca-116">Função auxiliar</span><span class="sxs-lookup"><span data-stu-id="086ca-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="086ca-117">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="086ca-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="086ca-118">(0..63)</span><span class="sxs-lookup"><span data-stu-id="086ca-118">(0..63)</span></span>   | <span data-ttu-id="086ca-119">Livrar</span><span class="sxs-lookup"><span data-stu-id="086ca-119">Rid</span></span>           | <span data-ttu-id="086ca-120">**IsridType**</span><span class="sxs-lookup"><span data-stu-id="086ca-120">**IsRidType**</span></span><br><span data-ttu-id="086ca-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="086ca-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="086ca-122">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="086ca-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="086ca-123">(64..95)</span><span class="sxs-lookup"><span data-stu-id="086ca-123">(64..95)</span></span> | <span data-ttu-id="086ca-124">Token codificado</span><span class="sxs-lookup"><span data-stu-id="086ca-124">Coded token</span></span> | <span data-ttu-id="086ca-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="086ca-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="086ca-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="086ca-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="086ca-127">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="086ca-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="086ca-128">Int16</span><span class="sxs-lookup"><span data-stu-id="086ca-128">Int16</span></span>         | <span data-ttu-id="086ca-129">**isFixedType**</span><span class="sxs-lookup"><span data-stu-id="086ca-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="086ca-130">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="086ca-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="086ca-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="086ca-131">UInt16</span></span>        | <span data-ttu-id="086ca-132">**isFixedType**</span><span class="sxs-lookup"><span data-stu-id="086ca-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="086ca-133">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="086ca-133">`iLONG` (98)</span></span>             | <span data-ttu-id="086ca-134">Int32</span><span class="sxs-lookup"><span data-stu-id="086ca-134">Int32</span></span>         | <span data-ttu-id="086ca-135">**isFixedType**</span><span class="sxs-lookup"><span data-stu-id="086ca-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="086ca-136">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="086ca-136">`iULONG` (99)</span></span>            | <span data-ttu-id="086ca-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="086ca-137">UInt32</span></span>        | <span data-ttu-id="086ca-138">**isFixedType**</span><span class="sxs-lookup"><span data-stu-id="086ca-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="086ca-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="086ca-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="086ca-140">Byte</span><span class="sxs-lookup"><span data-stu-id="086ca-140">Byte</span></span>          | <span data-ttu-id="086ca-141">**isFixedType**</span><span class="sxs-lookup"><span data-stu-id="086ca-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="086ca-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="086ca-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="086ca-143">String</span><span class="sxs-lookup"><span data-stu-id="086ca-143">String</span></span>        | <span data-ttu-id="086ca-144">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="086ca-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="086ca-145">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="086ca-145">`iGUID` (102)</span></span>            | <span data-ttu-id="086ca-146">Guid</span><span class="sxs-lookup"><span data-stu-id="086ca-146">Guid</span></span>          | <span data-ttu-id="086ca-147">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="086ca-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="086ca-148">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="086ca-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="086ca-149">Blob</span><span class="sxs-lookup"><span data-stu-id="086ca-149">Blob</span></span>          | <span data-ttu-id="086ca-150">**IsHeapType**</span><span class="sxs-lookup"><span data-stu-id="086ca-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="086ca-151">Os valores armazenados no *heap* (isto é, `IsHeapType == true`) podem ser lidos usando:</span><span class="sxs-lookup"><span data-stu-id="086ca-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="086ca-152">`iSTRING`: **IMetadataTables.GetString**</span><span class="sxs-lookup"><span data-stu-id="086ca-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="086ca-153">`iGUID`: **IMetadataTables.GetGUID**</span><span class="sxs-lookup"><span data-stu-id="086ca-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="086ca-154">`iBLOB`: **IMetadataTables.GetBlob**</span><span class="sxs-lookup"><span data-stu-id="086ca-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="086ca-155">Para usar as constantes definidas na `#define _DEFINE_META_DATA_META_CONSTANTS` tabela acima, inclua a diretiva fornecida pelo arquivo de cabeçalho *cor.h.*</span><span class="sxs-lookup"><span data-stu-id="086ca-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="086ca-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="086ca-156">Requirements</span></span>  
 <span data-ttu-id="086ca-157">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="086ca-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="086ca-158">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="086ca-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="086ca-159">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="086ca-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="086ca-160">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="086ca-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086ca-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="086ca-161">See also</span></span>

- [<span data-ttu-id="086ca-162">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="086ca-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="086ca-163">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="086ca-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
