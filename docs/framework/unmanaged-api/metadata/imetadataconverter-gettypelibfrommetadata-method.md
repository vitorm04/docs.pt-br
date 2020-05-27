---
title: Método IMetaDataConverter::GetTypeLibFromMetaData
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: 79bd8901641ee587e94861c0aec85b812591ea48
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008411"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="8ecc4-102">Método IMetaDataConverter::GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="8ecc4-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="8ecc4-103">Obtém um ponteiro para uma `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de módulo e biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="8ecc4-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ecc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ecc4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ecc4-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="8ecc4-106">no O nome do módulo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecc4-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="8ecc4-107">no O nome da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecc4-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="8ecc4-108">fora Um ponteiro para um local que recebe o endereço da `ITypeLib` instância que representa a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8ecc4-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ecc4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ecc4-109">Requirements</span></span>  
 <span data-ttu-id="8ecc4-110">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ecc4-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ecc4-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8ecc4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ecc4-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ecc4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ecc4-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ecc4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecc4-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ecc4-114">See also</span></span>

- [<span data-ttu-id="8ecc4-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="8ecc4-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
