---
title: Interface IMetaDataConverter
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: b771b368c069a4577d266b47bfb4a5ee1935e48e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436263"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="395ae-102">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="395ae-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="395ae-103">Fornece métodos para mapear bibliotecas de tipos para suas assinaturas de metadados e para converter de uma para a outra.</span><span class="sxs-lookup"><span data-stu-id="395ae-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="395ae-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="395ae-104">Methods</span></span>  
  
|<span data-ttu-id="395ae-105">Método</span><span class="sxs-lookup"><span data-stu-id="395ae-105">Method</span></span>|<span data-ttu-id="395ae-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="395ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="395ae-107">Método GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="395ae-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="395ae-108">Obtém um ponteiro para uma instância de [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) que representa a assinatura de metadados para a biblioteca de tipos referenciada pela instância de `ITypeInfo` especificada.</span><span class="sxs-lookup"><span data-stu-id="395ae-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="395ae-109">Método GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="395ae-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="395ae-110">Obtém um ponteiro para uma instância de `IMetaDataImport` que representa a assinatura de metadados para a biblioteca de tipos representada pela instância de `ITypeLib` especificada.</span><span class="sxs-lookup"><span data-stu-id="395ae-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="395ae-111">Método GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="395ae-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="395ae-112">Obtém um ponteiro para uma instância de `ITypeLib` que representa a biblioteca de tipos que tem o módulo e os nomes de biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="395ae-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="395ae-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="395ae-113">Requirements</span></span>  
 <span data-ttu-id="395ae-114">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="395ae-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="395ae-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="395ae-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="395ae-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="395ae-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="395ae-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="395ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395ae-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="395ae-118">See also</span></span>

- [<span data-ttu-id="395ae-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="395ae-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="395ae-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="395ae-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
