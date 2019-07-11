---
title: Método IMetaDataImport::GetInterfaceImplProps
ms.date: 02/25/2019
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
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782366"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="0878e-102">Método IMetaDataImport::GetInterfaceImplProps</span><span class="sxs-lookup"><span data-stu-id="0878e-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="0878e-103">Obtém um ponteiro para os tokens de metadados para o <xref:System.Type> que implementa o método especificado, e para a interface que declara esse método.</span><span class="sxs-lookup"><span data-stu-id="0878e-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0878e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0878e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0878e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0878e-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="0878e-106">[in] O token de metadados que representa o método para retornar os tokens de classe e interface para.</span><span class="sxs-lookup"><span data-stu-id="0878e-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="0878e-107">[out] O token de metadados que representa a classe que implementa o método.</span><span class="sxs-lookup"><span data-stu-id="0878e-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="0878e-108">[out] O token de metadados que representa a interface que define o método implementado.</span><span class="sxs-lookup"><span data-stu-id="0878e-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="0878e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0878e-109">Remarks</span></span>

 <span data-ttu-id="0878e-110">Obter o valor de `iImpl` chamando o [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0878e-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="0878e-111">Por exemplo, suponha que uma classe tem um `mdTypeDef` valor 0x02000007 e que ele implementa três interfaces cujos tipos têm tokens de token:</span><span class="sxs-lookup"><span data-stu-id="0878e-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="0878e-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="0878e-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="0878e-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="0878e-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="0878e-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="0878e-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="0878e-115">Conceitualmente, essas informações são armazenadas em uma tabela de implementação de interface como:</span><span class="sxs-lookup"><span data-stu-id="0878e-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="0878e-116">Número de linha</span><span class="sxs-lookup"><span data-stu-id="0878e-116">Row number</span></span> | <span data-ttu-id="0878e-117">Token de classe</span><span class="sxs-lookup"><span data-stu-id="0878e-117">Class token</span></span> | <span data-ttu-id="0878e-118">Token de interface</span><span class="sxs-lookup"><span data-stu-id="0878e-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="0878e-119">4</span><span class="sxs-lookup"><span data-stu-id="0878e-119">4</span></span>          |             |                 |
| <span data-ttu-id="0878e-120">5</span><span class="sxs-lookup"><span data-stu-id="0878e-120">5</span></span>          | <span data-ttu-id="0878e-121">02000007</span><span class="sxs-lookup"><span data-stu-id="0878e-121">02000007</span></span>    | <span data-ttu-id="0878e-122">02000003</span><span class="sxs-lookup"><span data-stu-id="0878e-122">02000003</span></span>        |
| <span data-ttu-id="0878e-123">6</span><span class="sxs-lookup"><span data-stu-id="0878e-123">6</span></span>          | <span data-ttu-id="0878e-124">02000007</span><span class="sxs-lookup"><span data-stu-id="0878e-124">02000007</span></span>    | <span data-ttu-id="0878e-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="0878e-125">0100000A</span></span>        |
| <span data-ttu-id="0878e-126">7</span><span class="sxs-lookup"><span data-stu-id="0878e-126">7</span></span>          |             |                 |
| <span data-ttu-id="0878e-127">8</span><span class="sxs-lookup"><span data-stu-id="0878e-127">8</span></span>          | <span data-ttu-id="0878e-128">02000007</span><span class="sxs-lookup"><span data-stu-id="0878e-128">02000007</span></span>    | <span data-ttu-id="0878e-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="0878e-129">0200001C</span></span>        |

<span data-ttu-id="0878e-130">Lembre-se de que o token é um valor de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="0878e-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="0878e-131">Inferiores a 3 bytes contêm o número de linha ou de RID.</span><span class="sxs-lookup"><span data-stu-id="0878e-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="0878e-132">O byte superior contém o tipo de token – 0x09 para `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="0878e-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="0878e-133">`GetInterfaceImplProps` Retorna as informações mantidas na linha cujo token que você fornecer no `iImpl` argumento.</span><span class="sxs-lookup"><span data-stu-id="0878e-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="0878e-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0878e-134">Requirements</span></span>  
 <span data-ttu-id="0878e-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0878e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0878e-136">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0878e-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0878e-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0878e-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0878e-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0878e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0878e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0878e-139">See also</span></span>

- [<span data-ttu-id="0878e-140">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0878e-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0878e-141">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0878e-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
