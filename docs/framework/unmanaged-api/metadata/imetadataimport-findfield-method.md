---
title: Método IMetaDataImport::FindField
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503660"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="70a2e-102">Método IMetaDataImport::FindField</span><span class="sxs-lookup"><span data-stu-id="70a2e-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="70a2e-103">Obtém um ponteiro para o token FieldDef do campo que está incluído pelo especificado <xref:System.Type> e que tem o nome e a assinatura de metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="70a2e-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a2e-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70a2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70a2e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="70a2e-106">no O token de TypeDef para a classe ou interface que inclui o campo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="70a2e-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="70a2e-107">Se esse valor for `mdTokenNil` , a pesquisa será feita para uma variável global.</span><span class="sxs-lookup"><span data-stu-id="70a2e-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="70a2e-108">no O nome do campo a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="70a2e-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="70a2e-109">no Um ponteiro para a assinatura de metadados binários do campo.</span><span class="sxs-lookup"><span data-stu-id="70a2e-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="70a2e-110">no O tamanho em bytes de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="70a2e-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="70a2e-111">fora Um ponteiro para o token FieldDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="70a2e-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70a2e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="70a2e-112">Remarks</span></span>  
 <span data-ttu-id="70a2e-113">Você especifica o campo usando sua classe ou interface delimitadora ( `td` ), seu nome ( `szName` ) e, opcionalmente, sua assinatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="70a2e-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="70a2e-114">A assinatura passada para `FindField` deve ter sido gerada no escopo atual, porque as assinaturas estão associadas a um escopo específico.</span><span class="sxs-lookup"><span data-stu-id="70a2e-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="70a2e-115">Uma assinatura pode inserir um token que identifica a classe de circunscrição ou o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="70a2e-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="70a2e-116">(O token é um índice na tabela de TypeDef local).</span><span class="sxs-lookup"><span data-stu-id="70a2e-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="70a2e-117">Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindField` .</span><span class="sxs-lookup"><span data-stu-id="70a2e-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="70a2e-118">`FindField`localiza somente os campos que foram definidos diretamente na classe ou interface; Ele não localiza campos herdados.</span><span class="sxs-lookup"><span data-stu-id="70a2e-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a2e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70a2e-119">Requirements</span></span>  
 <span data-ttu-id="70a2e-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a2e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a2e-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="70a2e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70a2e-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70a2e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70a2e-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a2e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a2e-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="70a2e-124">See also</span></span>

- [<span data-ttu-id="70a2e-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="70a2e-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="70a2e-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="70a2e-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
