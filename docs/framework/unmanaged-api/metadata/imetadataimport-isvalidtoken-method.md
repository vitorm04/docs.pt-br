---
title: Método IMetaDataImport::IsValidToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 9190d021b801be951d214406dde7e6d76da15608
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503431"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="08e26-102">Método IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="08e26-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="08e26-103">Obtém um valor que indica se o token especificado contém uma referência válida a um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="08e26-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08e26-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08e26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08e26-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="08e26-106">no O token para verificar a validade de referência.</span><span class="sxs-lookup"><span data-stu-id="08e26-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08e26-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="08e26-107">Return Value</span></span>  
 <span data-ttu-id="08e26-108">`true`Se `tk` é um token de metadados válido dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="08e26-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="08e26-109">Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="08e26-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08e26-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08e26-110">Requirements</span></span>  
 <span data-ttu-id="08e26-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08e26-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08e26-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="08e26-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08e26-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="08e26-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08e26-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08e26-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e26-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="08e26-115">See also</span></span>

- [<span data-ttu-id="08e26-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="08e26-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="08e26-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="08e26-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
