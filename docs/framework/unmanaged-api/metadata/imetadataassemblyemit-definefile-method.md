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
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008138"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="47b30-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="47b30-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="47b30-103">Cria uma `File` estrutura de metadados que contém metadados para o assembly referenciado por esse assembly e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="47b30-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47b30-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47b30-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47b30-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="47b30-106">no O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="47b30-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="47b30-107">no Um ponteiro para os dados de hash associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="47b30-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="47b30-108">no O tamanho em bytes de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="47b30-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="47b30-109">no Uma combinação de bits de `FileFlags` valores que especifica as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="47b30-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="47b30-110">fora Um ponteiro para o `File` token retornado.</span><span class="sxs-lookup"><span data-stu-id="47b30-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47b30-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="47b30-111">Remarks</span></span>  
 <span data-ttu-id="47b30-112">Uma `File` estrutura de metadados deve ser definida para cada arquivo que faz parte desse assembly no momento em que esse assembly foi criado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="47b30-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b30-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47b30-113">Requirements</span></span>  
 <span data-ttu-id="47b30-114">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47b30-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47b30-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="47b30-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47b30-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47b30-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47b30-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47b30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b30-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="47b30-118">See also</span></span>

- [<span data-ttu-id="47b30-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="47b30-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
