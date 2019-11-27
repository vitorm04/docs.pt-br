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
ms.openlocfilehash: 0464c61e4ff01483e10fb5708d5ed4b5f5ed63d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445238"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="e970c-102">Método IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="e970c-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="e970c-103">Obtém um valor que identifica a natureza do código no arquivo executável portátil (PE), normalmente um arquivo DLL ou EXE, que é definido no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="e970c-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e970c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e970c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e970c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e970c-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="e970c-106">fora Um ponteiro para um valor da enumeração [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) que descreve o arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="e970c-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="e970c-107">fora Um ponteiro para um valor que identifica a arquitetura do computador.</span><span class="sxs-lookup"><span data-stu-id="e970c-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="e970c-108">Consulte a próxima seção para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="e970c-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e970c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e970c-109">Remarks</span></span>  
 <span data-ttu-id="e970c-110">O valor referenciado pelo parâmetro `pdwMachine` pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="e970c-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="e970c-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e970c-111">Value</span></span>|<span data-ttu-id="e970c-112">Arquitetura do computador</span><span class="sxs-lookup"><span data-stu-id="e970c-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="e970c-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="e970c-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="e970c-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="e970c-114">0x014C</span></span>|<span data-ttu-id="e970c-115">x86</span><span class="sxs-lookup"><span data-stu-id="e970c-115">x86</span></span>|  
|<span data-ttu-id="e970c-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="e970c-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="e970c-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="e970c-117">0x0200</span></span>|<span data-ttu-id="e970c-118">IPF Intel</span><span class="sxs-lookup"><span data-stu-id="e970c-118">Intel IPF</span></span>|  
|<span data-ttu-id="e970c-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="e970c-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="e970c-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="e970c-120">0x8664</span></span>|<span data-ttu-id="e970c-121">X64</span><span class="sxs-lookup"><span data-stu-id="e970c-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e970c-122">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e970c-122">Requirements</span></span>  
 <span data-ttu-id="e970c-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e970c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e970c-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e970c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e970c-125">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e970c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e970c-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e970c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e970c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e970c-127">See also</span></span>

- [<span data-ttu-id="e970c-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e970c-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="e970c-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e970c-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e970c-130">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="e970c-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
