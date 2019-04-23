---
title: Método IMetaDataImport::GetCustomAttributeByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61029074347d554faaefe790c1e408e860e34690
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183021"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="ab7af-102">Método IMetaDataImport::GetCustomAttributeByName</span><span class="sxs-lookup"><span data-stu-id="ab7af-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="ab7af-103">Obtém o atributo personalizado, dado seu nome e proprietário.</span><span class="sxs-lookup"><span data-stu-id="ab7af-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab7af-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab7af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab7af-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ab7af-106">[in] Um token de metadados que representa o objeto que possui o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ab7af-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab7af-107">[in] O nome do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ab7af-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="ab7af-108">[out] Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ab7af-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="ab7af-109">[out] O tamanho em bytes dos dados retornados em \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="ab7af-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab7af-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab7af-110">Remarks</span></span>  
 <span data-ttu-id="ab7af-111">É permitido definir vários atributos personalizados para o mesmo proprietário; eles ainda podem ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="ab7af-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="ab7af-112">No entanto, `GetCustomAttributeByName` retorna apenas uma instância.</span><span class="sxs-lookup"><span data-stu-id="ab7af-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="ab7af-113">(`GetCustomAttributeByName` retorna a primeira instância que encontra.) Para localizar todas as instâncias de um atributo personalizado, chame o [imetadataimport:: Enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ab7af-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab7af-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab7af-114">Requirements</span></span>  
 <span data-ttu-id="ab7af-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab7af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab7af-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab7af-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab7af-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ab7af-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab7af-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7af-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab7af-119">See also</span></span>

- [<span data-ttu-id="ab7af-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ab7af-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ab7af-121">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ab7af-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
