---
title: Método IMetaDataImport::GetInterfaceImplProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91cb42a5bf1115de82b5fe28693cb77b66915c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600551"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="c7944-102">Método IMetaDataImport::GetInterfaceImplProps</span><span class="sxs-lookup"><span data-stu-id="c7944-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="c7944-103">Obtém um ponteiro para os tokens de metadados para o <xref:System.Type> que implementa o método especificado, e para a interface que declara esse método.</span><span class="sxs-lookup"><span data-stu-id="c7944-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7944-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7944-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7944-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7944-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="c7944-106">[in] O token de metadados que representa o método para retornar os tokens de classe e interface para.</span><span class="sxs-lookup"><span data-stu-id="c7944-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c7944-107">[out] O token de metadados que representa a classe que implementa o método.</span><span class="sxs-lookup"><span data-stu-id="c7944-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="c7944-108">[out] O token de metadados que representa a interface que define o método implementado.</span><span class="sxs-lookup"><span data-stu-id="c7944-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7944-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7944-109">Requirements</span></span>  
 <span data-ttu-id="c7944-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7944-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7944-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7944-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7944-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c7944-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7944-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7944-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7944-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7944-114">See also</span></span>
- [<span data-ttu-id="c7944-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c7944-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c7944-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c7944-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
