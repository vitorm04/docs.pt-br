---
title: Método IMetaDataImport2::GetPEKind
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d9dda1fb38546138d52b5fe61754d5497e676c37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113461"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="f5408-102">Método IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="f5408-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="f5408-103">Obtém um valor que identifica a natureza do código no executável portátil (PE) do arquivo, normalmente uma DLL ou EXE arquivo, que é definido no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="f5408-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5408-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5408-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5408-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5408-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="f5408-106">[out] Um ponteiro para um valor igual a [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeração que descreve o arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="f5408-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="f5408-107">[out] Um ponteiro para um valor que identifica a arquitetura do computador.</span><span class="sxs-lookup"><span data-stu-id="f5408-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="f5408-108">Consulte a próxima seção para os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="f5408-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5408-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5408-109">Remarks</span></span>  
 <span data-ttu-id="f5408-110">O valor referenciado pelo `pdwMachine` parâmetro pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="f5408-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="f5408-111">Valor</span><span class="sxs-lookup"><span data-stu-id="f5408-111">Value</span></span>|<span data-ttu-id="f5408-112">Arquitetura do computador</span><span class="sxs-lookup"><span data-stu-id="f5408-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="f5408-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="f5408-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="f5408-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="f5408-114">0x014C</span></span>|<span data-ttu-id="f5408-115">x86</span><span class="sxs-lookup"><span data-stu-id="f5408-115">x86</span></span>|  
|<span data-ttu-id="f5408-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="f5408-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="f5408-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="f5408-117">0x0200</span></span>|<span data-ttu-id="f5408-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="f5408-118">Intel IPF</span></span>|  
|<span data-ttu-id="f5408-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="f5408-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="f5408-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="f5408-120">0x8664</span></span>|<span data-ttu-id="f5408-121">X64</span><span class="sxs-lookup"><span data-stu-id="f5408-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5408-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5408-122">Requirements</span></span>  
 <span data-ttu-id="f5408-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5408-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5408-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f5408-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5408-125">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f5408-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f5408-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f5408-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5408-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5408-127">See also</span></span>

- [<span data-ttu-id="f5408-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f5408-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f5408-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f5408-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f5408-130">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="f5408-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
