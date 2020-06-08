---
title: Método IMetaDataTables::GetColumn
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 76d23fe9221ae5a07d79b8c5c1a7ad297922b003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501242"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="a99b9-102">Método IMetaDataTables::GetColumn</span><span class="sxs-lookup"><span data-stu-id="a99b9-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="a99b9-103">Obtém um ponteiro para o valor contido na célula da coluna e linha especificadas na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="a99b9-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a99b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a99b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a99b9-105">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="a99b9-106">no O índice da tabela.</span><span class="sxs-lookup"><span data-stu-id="a99b9-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="a99b9-107">no O índice da coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="a99b9-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="a99b9-108">no O índice da linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="a99b9-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="a99b9-109">fora Um ponteiro para o valor na célula.</span><span class="sxs-lookup"><span data-stu-id="a99b9-109">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="a99b9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a99b9-110">Remarks</span></span>

<span data-ttu-id="a99b9-111">A interpretação do valor retornado `pVal` depende do tipo da coluna.</span><span class="sxs-lookup"><span data-stu-id="a99b9-111">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="a99b9-112">O tipo de coluna pode ser determinado chamando [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="a99b9-112">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="a99b9-113">O método **GetColumn** converte automaticamente colunas do tipo **RID** ou **CodedToken** em valores completos de 32 bits `mdToken` .</span><span class="sxs-lookup"><span data-stu-id="a99b9-113">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="a99b9-114">Ele também converte automaticamente valores de 8 ou 16 bits em valores completos de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a99b9-114">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="a99b9-115">Para colunas do tipo *heap* , o *PVal* retornado será um índice no heap correspondente.</span><span class="sxs-lookup"><span data-stu-id="a99b9-115">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="a99b9-116">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="a99b9-116">Column type</span></span>              | <span data-ttu-id="a99b9-117">pVal contém</span><span class="sxs-lookup"><span data-stu-id="a99b9-117">pVal contains</span></span> | <span data-ttu-id="a99b9-118">Comentário</span><span class="sxs-lookup"><span data-stu-id="a99b9-118">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="a99b9-119">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="a99b9-119">`0`..`iRidMax`</span></span><br><span data-ttu-id="a99b9-120">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="a99b9-120">(0..63)</span></span>  | <span data-ttu-id="a99b9-121">mdToken</span><span class="sxs-lookup"><span data-stu-id="a99b9-121">mdToken</span></span>     | <span data-ttu-id="a99b9-122">*PVal* conterá um token completo.</span><span class="sxs-lookup"><span data-stu-id="a99b9-122">*pVal* will contain a full Token.</span></span> <span data-ttu-id="a99b9-123">A função converte automaticamente o RID em um token completo.</span><span class="sxs-lookup"><span data-stu-id="a99b9-123">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="a99b9-124">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="a99b9-124">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="a99b9-125">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="a99b9-125">(64..95)</span></span> | <span data-ttu-id="a99b9-126">mdToken</span><span class="sxs-lookup"><span data-stu-id="a99b9-126">mdToken</span></span> | <span data-ttu-id="a99b9-127">Após o retorno, o *PVal* conterá um token completo.</span><span class="sxs-lookup"><span data-stu-id="a99b9-127">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="a99b9-128">A função descompacta automaticamente o CodedToken em um token completo.</span><span class="sxs-lookup"><span data-stu-id="a99b9-128">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="a99b9-129">`iSHORT`(96)</span><span class="sxs-lookup"><span data-stu-id="a99b9-129">`iSHORT` (96)</span></span>            | <span data-ttu-id="a99b9-130">Int16</span><span class="sxs-lookup"><span data-stu-id="a99b9-130">Int16</span></span>         | <span data-ttu-id="a99b9-131">Faça automaticamente a extensão estendida para 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a99b9-131">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a99b9-132">`iUSHORT`(97)</span><span class="sxs-lookup"><span data-stu-id="a99b9-132">`iUSHORT` (97)</span></span>           | <span data-ttu-id="a99b9-133">UInt16</span><span class="sxs-lookup"><span data-stu-id="a99b9-133">UInt16</span></span>        | <span data-ttu-id="a99b9-134">Faça automaticamente a extensão estendida para 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a99b9-134">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a99b9-135">`iLONG`(98)</span><span class="sxs-lookup"><span data-stu-id="a99b9-135">`iLONG` (98)</span></span>             | <span data-ttu-id="a99b9-136">Int32</span><span class="sxs-lookup"><span data-stu-id="a99b9-136">Int32</span></span>         |                                        |
| <span data-ttu-id="a99b9-137">`iULONG`(99)</span><span class="sxs-lookup"><span data-stu-id="a99b9-137">`iULONG` (99)</span></span>            | <span data-ttu-id="a99b9-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="a99b9-138">UInt32</span></span>        |                                        |
| <span data-ttu-id="a99b9-139">`iBYTE`(100)</span><span class="sxs-lookup"><span data-stu-id="a99b9-139">`iBYTE` (100)</span></span>            | <span data-ttu-id="a99b9-140">Byte</span><span class="sxs-lookup"><span data-stu-id="a99b9-140">Byte</span></span>          | <span data-ttu-id="a99b9-141">Faça automaticamente a extensão estendida para 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a99b9-141">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="a99b9-142">`iSTRING`(101)</span><span class="sxs-lookup"><span data-stu-id="a99b9-142">`iSTRING` (101)</span></span>          | <span data-ttu-id="a99b9-143">Índice de heap de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a99b9-143">String heap index</span></span> | <span data-ttu-id="a99b9-144">*PVal* é um índice no heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a99b9-144">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="a99b9-145">Use [IMetadataTables:: GetString](imetadatatables-getstring-method.md) para obter o valor real da cadeia de caracteres da coluna.</span><span class="sxs-lookup"><span data-stu-id="a99b9-145">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="a99b9-146">`iGUID`(102)</span><span class="sxs-lookup"><span data-stu-id="a99b9-146">`iGUID` (102)</span></span>            | <span data-ttu-id="a99b9-147">Índice de heap de GUID</span><span class="sxs-lookup"><span data-stu-id="a99b9-147">Guid heap index</span></span> | <span data-ttu-id="a99b9-148">*PVal* é um índice no heap de GUID.</span><span class="sxs-lookup"><span data-stu-id="a99b9-148">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="a99b9-149">Use [IMetadataTables:: GetGUID](imetadatatables-getguid-method.md) para obter o valor de GUID de coluna real.</span><span class="sxs-lookup"><span data-stu-id="a99b9-149">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="a99b9-150">`iBLOB`(103)</span><span class="sxs-lookup"><span data-stu-id="a99b9-150">`iBLOB` (103)</span></span>            | <span data-ttu-id="a99b9-151">Índice de heap de BLOB</span><span class="sxs-lookup"><span data-stu-id="a99b9-151">Blob heap index</span></span> | <span data-ttu-id="a99b9-152">*PVal* é um índice no heap de BLOB.</span><span class="sxs-lookup"><span data-stu-id="a99b9-152">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="a99b9-153">Use [IMetadataTables:: getBlob](imetadatatables-getblob-method.md) para obter o valor de blob de coluna real.</span><span class="sxs-lookup"><span data-stu-id="a99b9-153">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="a99b9-154">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a99b9-154">Requirements</span></span>  
 <span data-ttu-id="a99b9-155">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a99b9-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a99b9-156">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a99b9-156">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a99b9-157">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a99b9-157">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a99b9-158">**Versões do .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a99b9-158">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99b9-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="a99b9-159">See also</span></span>

- [<span data-ttu-id="a99b9-160">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a99b9-160">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="a99b9-161">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a99b9-161">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
