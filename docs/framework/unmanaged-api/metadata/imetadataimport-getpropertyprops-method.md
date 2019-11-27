---
title: Método IMetaDataImport::GetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437063"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="4399d-102">Método IMetaDataImport::GetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="4399d-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="4399d-103">Obtém os metadados para a propriedade representada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4399d-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4399d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4399d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4399d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4399d-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="4399d-106">no Um token que representa a propriedade para a qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="4399d-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="4399d-107">fora Um ponteiro para o token de TypeDef que representa o tipo que implementa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="4399d-108">fora Um buffer para armazenar o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="4399d-109">no O tamanho em caracteres largos de `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="4399d-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="4399d-110">fora O número de caracteres largos retornados em `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="4399d-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="4399d-111">fora Um ponteiro para qualquer sinalizador de atributo aplicado à propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="4399d-112">Esse valor é um bitmask da enumeração [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4399d-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="4399d-113">fora Um ponteiro para a assinatura de metadados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="4399d-114">fora O número de bytes retornados em `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="4399d-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="4399d-115">fora Um sinalizador que especifica o tipo da constante que é o valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="4399d-116">Esse valor é da enumeração CorElementType.</span><span class="sxs-lookup"><span data-stu-id="4399d-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="4399d-117">fora Um ponteiro para os bytes que armazenam o valor padrão para essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="4399d-118">fora O tamanho em caracteres largos de `ppDefaultValue`, se `pdwCPlusTypeFlag` for ELEMENT_TYPE_STRING; caso contrário, esse valor não será relevante.</span><span class="sxs-lookup"><span data-stu-id="4399d-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="4399d-119">Nesse caso, o comprimento de `ppDefaultValue` é inferido do tipo especificado por `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="4399d-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="4399d-120">fora Um ponteiro para o token MethodDef que representa o método de acessador set para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="4399d-121">fora Um ponteiro para o token MethodDef que representa o método acessador get para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="4399d-122">fora Uma matriz de tokens MethodDef que representa outros métodos associados à propriedade.</span><span class="sxs-lookup"><span data-stu-id="4399d-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4399d-123">no O tamanho máximo da matriz de `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="4399d-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="4399d-124">Se você não fornecer uma matriz grande o suficiente para manter todos os métodos, eles serão ignorados sem aviso.</span><span class="sxs-lookup"><span data-stu-id="4399d-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="4399d-125">fora O número de tokens MethodDef retornados em `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="4399d-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4399d-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4399d-126">Requirements</span></span>  
 <span data-ttu-id="4399d-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4399d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4399d-128">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4399d-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4399d-129">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4399d-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4399d-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4399d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4399d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4399d-131">See also</span></span>

- [<span data-ttu-id="4399d-132">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4399d-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4399d-133">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4399d-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
