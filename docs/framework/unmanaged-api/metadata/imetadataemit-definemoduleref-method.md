---
title: Método IMetaDataEmit::DefineModuleRef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: efff491d92ac7910f43f76965ef98d1d0e4ba0aa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004420"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="52e36-102">Método IMetaDataEmit::DefineModuleRef</span><span class="sxs-lookup"><span data-stu-id="52e36-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="52e36-103">Cria a assinatura de metadados para um módulo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="52e36-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52e36-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52e36-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52e36-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="52e36-106">no O nome do outro arquivo de metadados, normalmente uma DLL.</span><span class="sxs-lookup"><span data-stu-id="52e36-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="52e36-107">Este é o nome do arquivo apenas.</span><span class="sxs-lookup"><span data-stu-id="52e36-107">This is the file name only.</span></span> <span data-ttu-id="52e36-108">Não use um nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="52e36-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="52e36-109">fora O `mdModuleRef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="52e36-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e36-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52e36-110">Requirements</span></span>  
 <span data-ttu-id="52e36-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e36-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e36-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52e36-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52e36-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52e36-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52e36-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e36-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="52e36-115">See also</span></span>

- [<span data-ttu-id="52e36-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="52e36-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="52e36-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="52e36-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
