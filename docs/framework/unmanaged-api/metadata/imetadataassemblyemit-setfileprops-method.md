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
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008060"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="c86c6-102">Método IMetaDataAssemblyEmit::SetFileProps</span><span class="sxs-lookup"><span data-stu-id="c86c6-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="c86c6-103">Modifica a estrutura de `File` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="c86c6-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c86c6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c86c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c86c6-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="c86c6-106">no O token de metadados que especifica a `File` estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="c86c6-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c86c6-107">no Um ponteiro para os dados de hash associados ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="c86c6-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c86c6-108">no O tamanho em bytes de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="c86c6-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="c86c6-109">no Uma combinação de bits de valores [CorFileFlags](corfileflags-enumeration.md) que especifica vários atributos do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c86c6-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c86c6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c86c6-110">Remarks</span></span>  
 <span data-ttu-id="c86c6-111">Para criar uma `File` estrutura de metadados, use o método [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c86c6-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c86c6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c86c6-112">Requirements</span></span>  
 <span data-ttu-id="c86c6-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c86c6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c86c6-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c86c6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c86c6-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c86c6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c86c6-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c86c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86c6-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c86c6-117">See also</span></span>

- [<span data-ttu-id="c86c6-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="c86c6-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
