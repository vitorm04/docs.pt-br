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
ms.openlocfilehash: 0d7dee3da1967f8a958ea95ab4555f279c962f51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451789"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="a82ce-102">Método IMetaDataTables::GetUserString</span><span class="sxs-lookup"><span data-stu-id="a82ce-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="a82ce-103">Obtém a cadeia de caracteres codificada no índice especificado na coluna de cadeia de caracteres no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="a82ce-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a82ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a82ce-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a82ce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a82ce-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="a82ce-106">[in] O valor de índice do qual a cadeia de caracteres codificada será recuperada.</span><span class="sxs-lookup"><span data-stu-id="a82ce-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="a82ce-107">[out] P; ponteiro para o tamanho do `ppData`.</span><span class="sxs-lookup"><span data-stu-id="a82ce-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a82ce-108">[out] Um ponteiro para um ponteiro para a cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="a82ce-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a82ce-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a82ce-109">Requirements</span></span>  
 <span data-ttu-id="a82ce-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a82ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a82ce-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a82ce-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a82ce-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a82ce-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a82ce-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a82ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a82ce-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a82ce-114">See Also</span></span>  
 [<span data-ttu-id="a82ce-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a82ce-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="a82ce-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a82ce-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
