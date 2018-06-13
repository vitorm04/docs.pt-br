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
ms.openlocfilehash: 29709a4297d53cc5e40daf732ac89751ead95152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449035"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="3a966-102">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="3a966-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="3a966-103">Fornece métodos para mapear as bibliotecas de tipo para suas assinaturas de metadados e para converter de um ao outro.</span><span class="sxs-lookup"><span data-stu-id="3a966-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a966-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a966-104">Methods</span></span>  
  
|<span data-ttu-id="3a966-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a966-105">Method</span></span>|<span data-ttu-id="3a966-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a966-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a966-107">Método GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="3a966-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="3a966-108">Obtém um ponteiro para um [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instância que representa a assinatura de metadados para a biblioteca de tipos referenciada por especificado `ITypeInfo` instância.</span><span class="sxs-lookup"><span data-stu-id="3a966-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="3a966-109">Método GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="3a966-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="3a966-110">Obtém um ponteiro para um `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pelo `ITypeLib` instância.</span><span class="sxs-lookup"><span data-stu-id="3a966-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="3a966-111">Método GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="3a966-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="3a966-112">Obtém um ponteiro para um `ITypeLib` instância que representa a biblioteca de tipos que tem os nomes de módulo e a biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="3a966-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a966-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a966-113">Requirements</span></span>  
 <span data-ttu-id="3a966-114">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a966-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a966-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a966-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a966-116">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a966-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a966-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a966-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a966-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a966-118">See Also</span></span>  
 [<span data-ttu-id="3a966-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="3a966-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="3a966-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3a966-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
