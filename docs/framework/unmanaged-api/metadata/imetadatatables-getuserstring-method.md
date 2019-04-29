---
title: Método IMetaDataTables::GetUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fefbab6b2ea9fbbfd90e03c41578a924f99c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645195"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="a9a61-102">Método IMetaDataTables::GetUserString</span><span class="sxs-lookup"><span data-stu-id="a9a61-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="a9a61-103">Obtém a cadeia de caracteres embutidos no índice especificado na coluna de cadeia de caracteres no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="a9a61-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9a61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9a61-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="a9a61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9a61-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="a9a61-106">[in] O valor de índice do qual a cadeia de caracteres embutidos será recuperada.</span><span class="sxs-lookup"><span data-stu-id="a9a61-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="a9a61-107">[out] Um ponteiro para o tamanho de `ppData`.</span><span class="sxs-lookup"><span data-stu-id="a9a61-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="a9a61-108">[out] Um ponteiro para um ponteiro para a cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="a9a61-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9a61-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9a61-109">Requirements</span></span>

<span data-ttu-id="a9a61-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9a61-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a9a61-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9a61-111">**Header:** Cor.h</span></span>

<span data-ttu-id="a9a61-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a9a61-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="a9a61-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a61-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a61-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9a61-114">See also</span></span>

- [<span data-ttu-id="a9a61-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a9a61-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="a9a61-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a9a61-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)