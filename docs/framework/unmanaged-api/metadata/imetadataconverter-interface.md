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
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008372"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="e9f4c-102">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="e9f4c-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="e9f4c-103">Fornece métodos para mapear bibliotecas de tipos para suas assinaturas de metadados e para converter de uma para a outra.</span><span class="sxs-lookup"><span data-stu-id="e9f4c-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9f4c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e9f4c-104">Methods</span></span>  
  
|<span data-ttu-id="e9f4c-105">Método</span><span class="sxs-lookup"><span data-stu-id="e9f4c-105">Method</span></span>|<span data-ttu-id="e9f4c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9f4c-107">Método GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="e9f4c-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="e9f4c-108">Obtém um ponteiro para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados para a biblioteca de tipos referenciada pela `ITypeInfo` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="e9f4c-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="e9f4c-109">Método GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="e9f4c-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="e9f4c-110">Obtém um ponteiro para uma `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pela `ITypeLib` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="e9f4c-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="e9f4c-111">Método GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="e9f4c-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="e9f4c-112">Obtém um ponteiro para uma `ITypeLib` instância que representa a biblioteca de tipos que tem o módulo e os nomes de biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="e9f4c-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9f4c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9f4c-113">Requirements</span></span>  
 <span data-ttu-id="e9f4c-114">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f4c-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f4c-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e9f4c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9f4c-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e9f4c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9f4c-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f4c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f4c-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9f4c-118">See also</span></span>

- [<span data-ttu-id="e9f4c-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="e9f4c-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="e9f4c-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e9f4c-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
