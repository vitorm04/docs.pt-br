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
ms.openlocfilehash: 7a2a5080872f49a84e36c53ac337d91738c15e45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501333"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="a851f-102">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="a851f-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="a851f-103">Fornece métodos para mapear bibliotecas de tipos para suas assinaturas de metadados e para converter de uma para a outra.</span><span class="sxs-lookup"><span data-stu-id="a851f-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a851f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a851f-104">Methods</span></span>  
  
|<span data-ttu-id="a851f-105">Método</span><span class="sxs-lookup"><span data-stu-id="a851f-105">Method</span></span>|<span data-ttu-id="a851f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a851f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a851f-107">Método GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="a851f-107">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="a851f-108">Obtém um ponteiro para uma instância de [IMetaDataImport](imetadataimport-interface.md) que representa a assinatura de metadados para a biblioteca de tipos referenciada pela `ITypeInfo` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="a851f-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="a851f-109">Método GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="a851f-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="a851f-110">Obtém um ponteiro para uma `IMetaDataImport` instância que representa a assinatura de metadados para a biblioteca de tipos representada pela `ITypeLib` instância especificada.</span><span class="sxs-lookup"><span data-stu-id="a851f-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="a851f-111">Método GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="a851f-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="a851f-112">Obtém um ponteiro para uma `ITypeLib` instância que representa a biblioteca de tipos que tem o módulo e os nomes de biblioteca especificados.</span><span class="sxs-lookup"><span data-stu-id="a851f-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a851f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a851f-113">Requirements</span></span>  
 <span data-ttu-id="a851f-114">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a851f-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a851f-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a851f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a851f-116">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a851f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a851f-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a851f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a851f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a851f-118">See also</span></span>

- [<span data-ttu-id="a851f-119">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="a851f-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="a851f-120">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a851f-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
