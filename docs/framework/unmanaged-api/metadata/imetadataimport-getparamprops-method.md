---
title: Método IMetaDataImport::GetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491050"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="d12f3-102">Método IMetaDataImport::GetParamProps</span><span class="sxs-lookup"><span data-stu-id="d12f3-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="d12f3-103">Obtém valores de metadados para o parâmetro referenciado pelo token ParamDef especificado.</span><span class="sxs-lookup"><span data-stu-id="d12f3-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d12f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d12f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d12f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d12f3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d12f3-106">no Um token ParamDef que representa o parâmetro para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="d12f3-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="d12f3-107">fora Um ponteiro para um token MethodDef que representa o método que usa o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d12f3-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="d12f3-108">fora A posição ordinal do parâmetro na lista de argumentos do método.</span><span class="sxs-lookup"><span data-stu-id="d12f3-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="d12f3-109">fora Um buffer para armazenar o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d12f3-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d12f3-110">no O tamanho solicitado em caracteres largos de `szName` .</span><span class="sxs-lookup"><span data-stu-id="d12f3-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d12f3-111">fora O tamanho retornado em caracteres largos de `szName` .</span><span class="sxs-lookup"><span data-stu-id="d12f3-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d12f3-112">fora Um ponteiro para qualquer sinalizador de atributo associado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d12f3-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="d12f3-113">Esta é uma bitmask de `CorParamAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="d12f3-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="d12f3-114">fora Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="d12f3-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d12f3-115">fora Um ponteiro para uma cadeia de caracteres constante retornada pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d12f3-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="d12f3-116">fora O tamanho de `ppValue` , em caracteres largos, ou zero se não `ppValue` mantiver uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d12f3-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d12f3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d12f3-117">Remarks</span></span>

<span data-ttu-id="d12f3-118">Os valores de sequência em `pulSequence` começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d12f3-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="d12f3-119">Um valor de retorno tem um número de sequência de 0.</span><span class="sxs-lookup"><span data-stu-id="d12f3-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="d12f3-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d12f3-120">Requirements</span></span>  
 <span data-ttu-id="d12f3-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d12f3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d12f3-122">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d12f3-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d12f3-123">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d12f3-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d12f3-124">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d12f3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d12f3-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="d12f3-125">See also</span></span>

- [<span data-ttu-id="d12f3-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d12f3-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d12f3-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d12f3-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
