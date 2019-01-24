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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc1f813cac237642fdaab653cd47552ab7472ab0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732916"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="5da9d-102">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="5da9d-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="5da9d-103">Fornece métodos para mapear as bibliotecas de tipos para suas assinaturas de metadados e para converter de um para outro.</span><span class="sxs-lookup"><span data-stu-id="5da9d-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5da9d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5da9d-104">Methods</span></span>  
  
|<span data-ttu-id="5da9d-105">Método</span><span class="sxs-lookup"><span data-stu-id="5da9d-105">Method</span></span>|<span data-ttu-id="5da9d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5da9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5da9d-107">Método GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="5da9d-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="5da9d-108">Obtém um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instância que representa a assinatura de metadados para a biblioteca de tipos referenciada pelo especificado `ITypeInfo` instância.</span><span class="sxs-lookup"><span data-stu-id="5da9d-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="5da9d-109">Método GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="5da9d-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="5da9d-110">Obtém um ponteiro para um `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pelo `ITypeLib` instância.</span><span class="sxs-lookup"><span data-stu-id="5da9d-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="5da9d-111">Método GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="5da9d-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="5da9d-112">Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de módulo e biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="5da9d-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5da9d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5da9d-113">Requirements</span></span>  
 <span data-ttu-id="5da9d-114">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5da9d-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da9d-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5da9d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5da9d-116">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5da9d-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5da9d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da9d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da9d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5da9d-118">See also</span></span>
- [<span data-ttu-id="5da9d-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="5da9d-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="5da9d-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5da9d-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
