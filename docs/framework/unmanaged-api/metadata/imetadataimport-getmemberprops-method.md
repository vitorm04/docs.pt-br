---
title: Método IMetaDataImport::GetMemberProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503634"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="efc79-102">Método IMetaDataImport::GetMemberProps</span><span class="sxs-lookup"><span data-stu-id="efc79-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="efc79-103">Obtém informações armazenadas nos metadados para uma definição de membro especificada, incluindo o nome, a assinatura binária e o endereço virtual relativo, do <xref:System.Type> membro referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="efc79-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="efc79-104">Este é um método auxiliar simples: se *MB* for um MethodDef, **GetMethodProps** será chamado; Se *MB* for um FieldDef, então **GetFieldProps** será chamado.</span><span class="sxs-lookup"><span data-stu-id="efc79-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="efc79-105">Consulte esses outros métodos para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="efc79-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="efc79-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efc79-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc79-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efc79-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="efc79-108">no O token que faz referência ao membro para obter os metadados associados.</span><span class="sxs-lookup"><span data-stu-id="efc79-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="efc79-109">fora Um ponteiro para o token de metadados que representa a classe do membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="efc79-110">fora O nome do membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="efc79-111">no O tamanho em caracteres largos do `szMember` buffer.</span><span class="sxs-lookup"><span data-stu-id="efc79-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="efc79-112">fora O tamanho em caracteres largos do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="efc79-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="efc79-113">fora Quaisquer valores de sinalizador aplicados ao membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="efc79-114">fora Um ponteiro para a assinatura de metadados binários do membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="efc79-115">fora O tamanho em bytes de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="efc79-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="efc79-116">fora Um ponteiro para o endereço virtual relativo do membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="efc79-117">fora Quaisquer sinalizadores de implementação de método associados ao membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="efc79-118">fora Um sinalizador que marca um <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="efc79-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="efc79-119">É um dos `ELEMENT_TYPE_*` valores.</span><span class="sxs-lookup"><span data-stu-id="efc79-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="efc79-120">fora Um valor de cadeia de caracteres constante retornado por este membro.</span><span class="sxs-lookup"><span data-stu-id="efc79-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="efc79-121">fora O tamanho em caracteres de `ppValue` , ou zero, se não `ppValue` mantiver uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="efc79-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc79-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efc79-122">Requirements</span></span>  
 <span data-ttu-id="efc79-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc79-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc79-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="efc79-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efc79-125">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efc79-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efc79-126">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc79-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc79-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="efc79-127">See also</span></span>

- [<span data-ttu-id="efc79-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="efc79-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="efc79-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="efc79-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
