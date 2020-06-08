---
title: Interface IMetaDataTables
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 2105033e684ec172e24adfb14bcab7668b388af3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501115"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="ca625-102">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ca625-102">IMetaDataTables Interface</span></span>
<span data-ttu-id="ca625-103">Fornece métodos para o armazenamento e a recuperação de informações de metadados em tabelas.</span><span class="sxs-lookup"><span data-stu-id="ca625-103">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca625-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ca625-104">Methods</span></span>  
  
|<span data-ttu-id="ca625-105">Método</span><span class="sxs-lookup"><span data-stu-id="ca625-105">Method</span></span>|<span data-ttu-id="ca625-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca625-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca625-107">Método GetBlob</span><span class="sxs-lookup"><span data-stu-id="ca625-107">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="ca625-108">Obtém um ponteiro para o objeto binário grande (BLOB) no índice de coluna especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-108">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="ca625-109">Método GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="ca625-109">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="ca625-110">Obtém o tamanho, em bytes, do heap de BLOB.</span><span class="sxs-lookup"><span data-stu-id="ca625-110">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="ca625-111">Método GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="ca625-111">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="ca625-112">Obtém um ponteiro para uma matriz de tokens associados ao índice de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-112">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="ca625-113">Método GetColumn</span><span class="sxs-lookup"><span data-stu-id="ca625-113">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="ca625-114">Obtém um ponteiro para os valores contidos na coluna no índice de coluna especificado, na tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-114">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="ca625-115">Método GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="ca625-115">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="ca625-116">Obtém dados sobre a coluna especificada na tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="ca625-116">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="ca625-117">Método GetGuid</span><span class="sxs-lookup"><span data-stu-id="ca625-117">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="ca625-118">Obtém um GUID da linha no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-118">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="ca625-119">Método GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="ca625-119">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="ca625-120">Obtém o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="ca625-120">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="ca625-121">Método GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="ca625-121">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="ca625-122">Obtém o índice do próximo BLOB na tabela.</span><span class="sxs-lookup"><span data-stu-id="ca625-122">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="ca625-123">Método GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="ca625-123">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="ca625-124">Obtém o índice do próximo valor de GUID na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-124">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="ca625-125">Método GetNextString</span><span class="sxs-lookup"><span data-stu-id="ca625-125">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="ca625-126">Obtém o índice da próxima cadeia de caracteres na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-126">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="ca625-127">Método GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="ca625-127">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="ca625-128">Obtém o índice da linha que contém a próxima cadeia de caracteres embutida em código na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-128">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="ca625-129">Método GetNumTables</span><span class="sxs-lookup"><span data-stu-id="ca625-129">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="ca625-130">Obtém o número de tabelas no escopo da `IMetaDataTables` instância atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-130">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="ca625-131">Método GetRow</span><span class="sxs-lookup"><span data-stu-id="ca625-131">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="ca625-132">Obtém a linha no índice de linha especificado, na tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-132">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="ca625-133">Método GetString</span><span class="sxs-lookup"><span data-stu-id="ca625-133">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="ca625-134">Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo de referência atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-134">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="ca625-135">Método GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="ca625-135">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="ca625-136">Obtém o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca625-136">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="ca625-137">Método GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="ca625-137">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="ca625-138">Obtém o índice da tabela referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-138">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="ca625-139">Método GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="ca625-139">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="ca625-140">Obtém o nome, o tamanho da linha, o número de linhas, o número de colunas e o índice da coluna de chave da tabela no índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="ca625-140">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="ca625-141">Método GetUserString</span><span class="sxs-lookup"><span data-stu-id="ca625-141">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="ca625-142">Obtém a cadeia de caracteres embutida em código no índice especificado na coluna de cadeia de caracteres no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="ca625-142">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="ca625-143">Método GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="ca625-143">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="ca625-144">Obtém o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="ca625-144">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca625-145">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca625-145">Requirements</span></span>  
 <span data-ttu-id="ca625-146">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca625-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca625-147">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ca625-147">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca625-148">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca625-148">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca625-149">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca625-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca625-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca625-150">See also</span></span>

- [<span data-ttu-id="ca625-151">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="ca625-151">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="ca625-152">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ca625-152">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
