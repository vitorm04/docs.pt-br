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
ms.openlocfilehash: 106ffeee521f69a73628b1fb6a611abc733583f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431877"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="f3a94-102">Método IMetaDataAssemblyEmit::SetFileProps</span><span class="sxs-lookup"><span data-stu-id="f3a94-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="f3a94-103">Modifica a estrutura de metadados de `File` especificada.</span><span class="sxs-lookup"><span data-stu-id="f3a94-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3a94-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3a94-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3a94-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="f3a94-106">no O token de metadados que especifica a estrutura de metadados `File` a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="f3a94-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f3a94-107">no Um ponteiro para os dados de hash associados ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="f3a94-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f3a94-108">no O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f3a94-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f3a94-109">no Uma combinação de bits de valores [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) que especifica vários atributos do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f3a94-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3a94-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3a94-110">Remarks</span></span>  
 <span data-ttu-id="f3a94-111">Para criar uma estrutura de metadados `File`, use o método [IMetaDataAssemblyEmit::D efinefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f3a94-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a94-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3a94-112">Requirements</span></span>  
 <span data-ttu-id="f3a94-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a94-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a94-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3a94-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3a94-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3a94-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3a94-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a94-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3a94-117">See also</span></span>

- [<span data-ttu-id="f3a94-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f3a94-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
