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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0c2da234fa89bbf92c2117d6428d64502da0c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044739"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="818cb-102">Método IMetaDataAssemblyEmit::SetFileProps</span><span class="sxs-lookup"><span data-stu-id="818cb-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="818cb-103">Modifica especificado `File` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="818cb-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="818cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="818cb-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="818cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="818cb-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="818cb-106">[in] O token de metadados que especifica o `File` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="818cb-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="818cb-107">[in] Um ponteiro para o hash de dados associado ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="818cb-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="818cb-108">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="818cb-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="818cb-109">[in] Uma combinação bit a bit de [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores que especificam vários atributos do arquivo.</span><span class="sxs-lookup"><span data-stu-id="818cb-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="818cb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="818cb-110">Remarks</span></span>  
 <span data-ttu-id="818cb-111">Para criar uma `File` estrutura de metadados, use o [imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="818cb-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="818cb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="818cb-112">Requirements</span></span>  
 <span data-ttu-id="818cb-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="818cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="818cb-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="818cb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="818cb-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="818cb-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="818cb-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="818cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818cb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="818cb-117">See also</span></span>

- [<span data-ttu-id="818cb-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="818cb-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
