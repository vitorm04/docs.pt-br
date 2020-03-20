---
title: Método IMetaDataAssemblyEmit::SetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176026"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="89764-102">Método IMetaDataAssemblyEmit::SetFileProps</span><span class="sxs-lookup"><span data-stu-id="89764-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="89764-103">Modifica a estrutura `File` de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="89764-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89764-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89764-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89764-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="89764-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="89764-106">[em] O token de metadados `File` que especifica a estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="89764-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="89764-107">[em] Um ponteiro para os dados hash associados ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="89764-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="89764-108">[em] O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="89764-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="89764-109">[em] Uma combinação bitwise de valores [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) que especificam vários atributos do arquivo.</span><span class="sxs-lookup"><span data-stu-id="89764-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89764-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="89764-110">Remarks</span></span>  
 <span data-ttu-id="89764-111">Para criar `File` uma estrutura de metadados, use o método [IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)</span><span class="sxs-lookup"><span data-stu-id="89764-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89764-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89764-112">Requirements</span></span>  
 <span data-ttu-id="89764-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89764-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89764-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89764-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89764-115">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89764-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89764-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89764-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89764-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="89764-117">See also</span></span>

- [<span data-ttu-id="89764-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="89764-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
