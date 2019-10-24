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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774254"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="d1284-102">Método IMetaDataTables::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="d1284-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="d1284-103">Obtém dados sobre a coluna especificada na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="d1284-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1284-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1284-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d1284-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1284-105">Parameters</span></span>
=======

 `ixTbl`  
 <span data-ttu-id="d1284-106">no O índice da tabela desejada.</span><span class="sxs-lookup"><span data-stu-id="d1284-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="d1284-107">no O índice da coluna desejada.</span><span class="sxs-lookup"><span data-stu-id="d1284-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="d1284-108">fora Um ponteiro para o deslocamento da coluna na linha.</span><span class="sxs-lookup"><span data-stu-id="d1284-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="d1284-109">fora Um ponteiro para o tamanho, em bytes, da coluna.</span><span class="sxs-lookup"><span data-stu-id="d1284-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="d1284-110">fora Um ponteiro para o tipo dos valores na coluna.</span><span class="sxs-lookup"><span data-stu-id="d1284-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="d1284-111">fora Um ponteiro para um ponteiro para o nome da coluna.</span><span class="sxs-lookup"><span data-stu-id="d1284-111">[out] A pointer to a pointer to the column name.</span></span>  
 
## <a name="remarks"></a><span data-ttu-id="d1284-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1284-112">Remarks</span></span>

<span data-ttu-id="d1284-113">O tipo de coluna retornado cai dentro de um intervalo de valores:</span><span class="sxs-lookup"><span data-stu-id="d1284-113">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="d1284-114">pType</span><span class="sxs-lookup"><span data-stu-id="d1284-114">pType</span></span>                    | <span data-ttu-id="d1284-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1284-115">Description</span></span>   | <span data-ttu-id="d1284-116">Função auxiliar</span><span class="sxs-lookup"><span data-stu-id="d1284-116">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="d1284-117">`0`.. `iRidMax`</span><span class="sxs-lookup"><span data-stu-id="d1284-117">`0`..`iRidMax`</span></span><br><span data-ttu-id="d1284-118">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="d1284-118">(0..63)</span></span>   | <span data-ttu-id="d1284-119">Eliminá</span><span class="sxs-lookup"><span data-stu-id="d1284-119">Rid</span></span>           | <span data-ttu-id="d1284-120">**IsRidType**</span><span class="sxs-lookup"><span data-stu-id="d1284-120">**IsRidType**</span></span><br><span data-ttu-id="d1284-121">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="d1284-121">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d1284-122">`iCodedToken`.. `iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="d1284-122">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="d1284-123">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="d1284-123">(64..95)</span></span> | <span data-ttu-id="d1284-124">Token codificado</span><span class="sxs-lookup"><span data-stu-id="d1284-124">Coded token</span></span> | <span data-ttu-id="d1284-125">**IsCodedTokenType**</span><span class="sxs-lookup"><span data-stu-id="d1284-125">**IsCodedTokenType**</span></span> <br><span data-ttu-id="d1284-126">**IsRidOrToken**</span><span class="sxs-lookup"><span data-stu-id="d1284-126">**IsRidOrToken**</span></span> |
| <span data-ttu-id="d1284-127">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="d1284-127">`iSHORT` (96)</span></span>            | <span data-ttu-id="d1284-128">Int16</span><span class="sxs-lookup"><span data-stu-id="d1284-128">Int16</span></span>         | <span data-ttu-id="d1284-129">**Isfixatype**</span><span class="sxs-lookup"><span data-stu-id="d1284-129">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d1284-130">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="d1284-130">`iUSHORT` (97)</span></span>           | <span data-ttu-id="d1284-131">UInt16</span><span class="sxs-lookup"><span data-stu-id="d1284-131">UInt16</span></span>        | <span data-ttu-id="d1284-132">**Isfixatype**</span><span class="sxs-lookup"><span data-stu-id="d1284-132">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d1284-133">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="d1284-133">`iLONG` (98)</span></span>             | <span data-ttu-id="d1284-134">Int32</span><span class="sxs-lookup"><span data-stu-id="d1284-134">Int32</span></span>         | <span data-ttu-id="d1284-135">**Isfixatype**</span><span class="sxs-lookup"><span data-stu-id="d1284-135">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d1284-136">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="d1284-136">`iULONG` (99)</span></span>            | <span data-ttu-id="d1284-137">UInt32</span><span class="sxs-lookup"><span data-stu-id="d1284-137">UInt32</span></span>        | <span data-ttu-id="d1284-138">**Isfixatype**</span><span class="sxs-lookup"><span data-stu-id="d1284-138">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d1284-139">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="d1284-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="d1284-140">Byte</span><span class="sxs-lookup"><span data-stu-id="d1284-140">Byte</span></span>          | <span data-ttu-id="d1284-141">**Isfixatype**</span><span class="sxs-lookup"><span data-stu-id="d1284-141">**IsFixedType**</span></span>                   |
| <span data-ttu-id="d1284-142">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="d1284-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="d1284-143">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="d1284-143">String</span></span>        | <span data-ttu-id="d1284-144">**Isheaptype**</span><span class="sxs-lookup"><span data-stu-id="d1284-144">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d1284-145">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="d1284-145">`iGUID` (102)</span></span>            | <span data-ttu-id="d1284-146">GUID</span><span class="sxs-lookup"><span data-stu-id="d1284-146">Guid</span></span>          | <span data-ttu-id="d1284-147">**Isheaptype**</span><span class="sxs-lookup"><span data-stu-id="d1284-147">**IsHeapType**</span></span>                    |
| <span data-ttu-id="d1284-148">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="d1284-148">`iBLOB` (103)</span></span>            | <span data-ttu-id="d1284-149">Blob</span><span class="sxs-lookup"><span data-stu-id="d1284-149">Blob</span></span>          | <span data-ttu-id="d1284-150">**Isheaptype**</span><span class="sxs-lookup"><span data-stu-id="d1284-150">**IsHeapType**</span></span>                    |

<span data-ttu-id="d1284-151">Os valores que são armazenados no *heap* (ou seja, `IsHeapType == true`) podem ser lidos usando:</span><span class="sxs-lookup"><span data-stu-id="d1284-151">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="d1284-152">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="d1284-152">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="d1284-153">`iGUID`: **IMetadataTables. GETguid**</span><span class="sxs-lookup"><span data-stu-id="d1284-153">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="d1284-154">`iBLOB`: **IMetadataTables. getBlob**</span><span class="sxs-lookup"><span data-stu-id="d1284-154">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1284-155">Para usar as constantes definidas na tabela acima, inclua a diretiva `#define _DEFINE_META_DATA_META_CONSTANTS` fornecida pelo arquivo de cabeçalho *cor. h* .</span><span class="sxs-lookup"><span data-stu-id="d1284-155">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1284-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1284-156">Requirements</span></span>  
 <span data-ttu-id="d1284-157">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1284-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1284-158">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1284-158">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1284-159">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d1284-159">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1284-160">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1284-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1284-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1284-161">See also</span></span>

- [<span data-ttu-id="d1284-162">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="d1284-162">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d1284-163">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="d1284-163">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
