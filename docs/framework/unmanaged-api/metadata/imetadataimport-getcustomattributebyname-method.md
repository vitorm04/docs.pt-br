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
ms.openlocfilehash: 7bebf254110d9970ff3a99f948ff2e831ffb6b35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782431"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="aa676-102">Método IMetaDataImport::GetCustomAttributeByName</span><span class="sxs-lookup"><span data-stu-id="aa676-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="aa676-103">Obtém o atributo personalizado, dado seu nome e proprietário.</span><span class="sxs-lookup"><span data-stu-id="aa676-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa676-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa676-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa676-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa676-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="aa676-106">[in] Um token de metadados que representa o objeto que possui o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aa676-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="aa676-107">[in] O nome do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aa676-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="aa676-108">[out] Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="aa676-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="aa676-109">[out] O tamanho em bytes dos dados retornados em \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="aa676-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa676-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa676-110">Remarks</span></span>  
 <span data-ttu-id="aa676-111">É permitido definir vários atributos personalizados para o mesmo proprietário; eles ainda podem ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="aa676-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="aa676-112">No entanto, `GetCustomAttributeByName` retorna apenas uma instância.</span><span class="sxs-lookup"><span data-stu-id="aa676-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="aa676-113">(`GetCustomAttributeByName` retorna a primeira instância que encontra.) Para localizar todas as instâncias de um atributo personalizado, chame o [imetadataimport:: Enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="aa676-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa676-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa676-114">Requirements</span></span>  
 <span data-ttu-id="aa676-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa676-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa676-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa676-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa676-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="aa676-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa676-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa676-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa676-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa676-119">See also</span></span>

- [<span data-ttu-id="aa676-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="aa676-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="aa676-121">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="aa676-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
