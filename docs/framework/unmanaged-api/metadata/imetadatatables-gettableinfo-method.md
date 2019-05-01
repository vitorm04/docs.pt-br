---
title: Método IMetaDataTables::GetTableInfo
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82c88c75d5799134d8c683c91e28f956743b84ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992219"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="ceb91-102">Método IMetaDataTables::GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="ceb91-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="ceb91-103">Obtém o nome, tamanho da linha, número de linhas, o número de colunas e o índice da coluna de chave da tabela especificada.</span><span class="sxs-lookup"><span data-stu-id="ceb91-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ceb91-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ceb91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ceb91-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ceb91-106">[in] O identificador da tabela cujas propriedades a serem retornadas.</span><span class="sxs-lookup"><span data-stu-id="ceb91-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="ceb91-107">[out] Um ponteiro para o tamanho, em bytes, de uma linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="ceb91-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="ceb91-108">[out] Um ponteiro para o número de linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="ceb91-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="ceb91-109">[out] Um ponteiro para o número de colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="ceb91-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="ceb91-110">[out] Um ponteiro para o índice da coluna de chave, ou -1 se a tabela não tiver nenhuma coluna de chave.</span><span class="sxs-lookup"><span data-stu-id="ceb91-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ceb91-111">[out] Um ponteiro para um ponteiro para o nome da tabela.</span><span class="sxs-lookup"><span data-stu-id="ceb91-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceb91-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ceb91-112">Requirements</span></span>  
 <span data-ttu-id="ceb91-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb91-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb91-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ceb91-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ceb91-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ceb91-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ceb91-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb91-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb91-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceb91-117">See also</span></span>

- [<span data-ttu-id="ceb91-118">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ceb91-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ceb91-119">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ceb91-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
