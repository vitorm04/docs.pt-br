---
title: "Método IMetaDataTables::GetTableInfo"
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
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ce9e3beb15724c7d7ddf02cbe7f83795d474139
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="16a98-102">Método IMetaDataTables::GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="16a98-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="16a98-103">Obtém o nome, o tamanho de linha, o número de linhas, o número de colunas e o índice da coluna de chave da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="16a98-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16a98-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16a98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16a98-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="16a98-106">[in] O identificador da tabela cujas propriedades para retornar.</span><span class="sxs-lookup"><span data-stu-id="16a98-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="16a98-107">[out] Um ponteiro para o tamanho, em bytes, de uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="16a98-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="16a98-108">[out] Um ponteiro para o número de linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="16a98-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="16a98-109">[out] Um ponteiro para o número de colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="16a98-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="16a98-110">[out] Um ponteiro para o índice da coluna de chave, ou -1 se a tabela não tiver nenhuma coluna de chave.</span><span class="sxs-lookup"><span data-stu-id="16a98-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="16a98-111">[out] Um ponteiro para um ponteiro para o nome da tabela.</span><span class="sxs-lookup"><span data-stu-id="16a98-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16a98-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16a98-112">Requirements</span></span>  
 <span data-ttu-id="16a98-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16a98-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a98-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16a98-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16a98-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="16a98-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16a98-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a98-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a98-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16a98-117">See Also</span></span>  
 [<span data-ttu-id="16a98-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="16a98-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="16a98-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="16a98-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
