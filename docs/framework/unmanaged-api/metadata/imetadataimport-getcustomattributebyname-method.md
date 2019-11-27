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
ms.openlocfilehash: bd7ba7ff10918e5953ea8ae89a60af3115af48a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437690"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="bdaf8-102">Método IMetaDataImport::GetCustomAttributeByName</span><span class="sxs-lookup"><span data-stu-id="bdaf8-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="bdaf8-103">Obtém o atributo personalizado, dado seu nome e proprietário.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdaf8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdaf8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdaf8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdaf8-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="bdaf8-106">no Um token de metadados que representa o objeto que possui o atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="bdaf8-107">no O nome do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="bdaf8-108">fora Um ponteiro para uma matriz de dados que é o valor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="bdaf8-109">fora O tamanho em bytes dos dados retornados em \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdaf8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdaf8-110">Remarks</span></span>  
 <span data-ttu-id="bdaf8-111">É legal definir vários atributos personalizados para o mesmo proprietário; Eles podem até mesmo ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="bdaf8-112">No entanto, `GetCustomAttributeByName` retorna apenas uma instância.</span><span class="sxs-lookup"><span data-stu-id="bdaf8-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="bdaf8-113">(`GetCustomAttributeByName` retorna a primeira instância que ele encontra.) Para localizar todas as instâncias de um atributo personalizado, chame o método [IMetaDataImport:: EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bdaf8-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdaf8-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bdaf8-114">Requirements</span></span>  
 <span data-ttu-id="bdaf8-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdaf8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdaf8-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bdaf8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdaf8-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bdaf8-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdaf8-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdaf8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdaf8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdaf8-119">See also</span></span>

- [<span data-ttu-id="bdaf8-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bdaf8-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bdaf8-121">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bdaf8-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
