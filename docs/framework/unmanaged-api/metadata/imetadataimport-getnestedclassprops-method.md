---
title: Método IMetaDataImport::GetNestedClassProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503530"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="e3a61-102">Método IMetaDataImport::GetNestedClassProps</span><span class="sxs-lookup"><span data-stu-id="e3a61-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="e3a61-103">Obtém o token de TypeDef para o pai <xref:System.Type> do tipo aninhado especificado.</span><span class="sxs-lookup"><span data-stu-id="e3a61-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3a61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3a61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3a61-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="e3a61-106">no Um token de TypeDef que representa o <xref:System.Type> para retornar o token de classe pai para.</span><span class="sxs-lookup"><span data-stu-id="e3a61-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="e3a61-107">fora Um ponteiro para o token de TypeDef para o <xref:System.Type> que `tdNestedClass` está aninhado em.</span><span class="sxs-lookup"><span data-stu-id="e3a61-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a61-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3a61-108">Requirements</span></span>  
 <span data-ttu-id="e3a61-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a61-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a61-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e3a61-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3a61-111">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3a61-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3a61-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a61-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a61-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3a61-113">See also</span></span>

- [<span data-ttu-id="e3a61-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e3a61-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e3a61-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e3a61-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
