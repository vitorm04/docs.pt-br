---
title: Método IMetaDataImport::GetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: a031cdb875b5eb046428d4d235d3093caddb7a6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491271"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="b72ad-102">Método IMetaDataImport::GetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="b72ad-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="b72ad-103">Obtém um ponteiro para o tipo nativo não gerenciado do campo representado pelo token de metadados do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="b72ad-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b72ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b72ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b72ad-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b72ad-106">no O token de metadados que representa o campo para obter informações de marshaling de interoperabilidade para.</span><span class="sxs-lookup"><span data-stu-id="b72ad-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="b72ad-107">fora Um ponteiro para a assinatura de metadados do tipo nativo do campo.</span><span class="sxs-lookup"><span data-stu-id="b72ad-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="b72ad-108">fora O tamanho em bytes de `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="b72ad-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b72ad-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b72ad-109">Requirements</span></span>  
 <span data-ttu-id="b72ad-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b72ad-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b72ad-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b72ad-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b72ad-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b72ad-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b72ad-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72ad-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b72ad-114">See also</span></span>

- [<span data-ttu-id="b72ad-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b72ad-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b72ad-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b72ad-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
