---
title: Método IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440214"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="f5d13-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="f5d13-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="f5d13-103">Cria uma estrutura de metadados `File` que contém metadados para o assembly referenciado por esse assembly e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="f5d13-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5d13-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5d13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5d13-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f5d13-106">no O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="f5d13-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f5d13-107">no Um ponteiro para os dados de hash associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="f5d13-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f5d13-108">no O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f5d13-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="f5d13-109">no Uma combinação de bits de `FileFlags` de valores que especifica configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f5d13-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="f5d13-110">fora Um ponteiro para o token de `File` retornado.</span><span class="sxs-lookup"><span data-stu-id="f5d13-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5d13-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5d13-111">Remarks</span></span>  
 <span data-ttu-id="f5d13-112">Uma estrutura de metadados `File` deve ser definida para cada arquivo que faz parte desse assembly no momento em que esse assembly foi criado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="f5d13-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d13-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f5d13-113">Requirements</span></span>  
 <span data-ttu-id="f5d13-114">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d13-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d13-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5d13-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5d13-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5d13-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5d13-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d13-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d13-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5d13-118">See also</span></span>

- [<span data-ttu-id="f5d13-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f5d13-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
