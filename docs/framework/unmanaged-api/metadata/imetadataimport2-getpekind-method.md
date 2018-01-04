---
title: "Método IMetaDataImport2::GetPEKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8dc31877ba3550fa8faf610b831dfd2e7b313ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="85c7e-102">Método IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="85c7e-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="85c7e-103">Obtém um valor que identifica a natureza do código de PE (executável portátil) de arquivo, geralmente um arquivo DLL ou EXE, que é definido no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="85c7e-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85c7e-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85c7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85c7e-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="85c7e-106">[out] Um ponteiro para um valor de [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeração que descreve o arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="85c7e-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="85c7e-107">[out] Um ponteiro para um valor que identifica a arquitetura da máquina.</span><span class="sxs-lookup"><span data-stu-id="85c7e-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="85c7e-108">Consulte a próxima seção para os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="85c7e-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85c7e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="85c7e-109">Remarks</span></span>  
 <span data-ttu-id="85c7e-110">O valor referenciado pelo `pdwMachine` parâmetro pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="85c7e-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="85c7e-111">Valor</span><span class="sxs-lookup"><span data-stu-id="85c7e-111">Value</span></span>|<span data-ttu-id="85c7e-112">Arquitetura do computador</span><span class="sxs-lookup"><span data-stu-id="85c7e-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="85c7e-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="85c7e-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="85c7e-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="85c7e-114">0x014C</span></span>|<span data-ttu-id="85c7e-115">x86</span><span class="sxs-lookup"><span data-stu-id="85c7e-115">x86</span></span>|  
|<span data-ttu-id="85c7e-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="85c7e-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="85c7e-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="85c7e-117">0x0200</span></span>|<span data-ttu-id="85c7e-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="85c7e-118">Intel IPF</span></span>|  
|<span data-ttu-id="85c7e-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="85c7e-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="85c7e-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="85c7e-120">0x8664</span></span>|<span data-ttu-id="85c7e-121">X64</span><span class="sxs-lookup"><span data-stu-id="85c7e-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85c7e-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85c7e-122">Requirements</span></span>  
 <span data-ttu-id="85c7e-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c7e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c7e-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85c7e-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85c7e-125">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="85c7e-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85c7e-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c7e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c7e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85c7e-127">See Also</span></span>  
 [<span data-ttu-id="85c7e-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="85c7e-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="85c7e-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="85c7e-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="85c7e-130">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="85c7e-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
