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
ms.openlocfilehash: c938ef8783a122dec2a5f5bd3775661d68fba62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449397"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="fc8bd-102">Método IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="fc8bd-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="fc8bd-103">Obtém um valor que identifica a natureza do código de PE (executável portátil) de arquivo, geralmente um arquivo DLL ou EXE, que é definido no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc8bd-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc8bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc8bd-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="fc8bd-106">[out] Um ponteiro para um valor de [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeração que descreve o arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="fc8bd-107">[out] Um ponteiro para um valor que identifica a arquitetura da máquina.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="fc8bd-108">Consulte a próxima seção para os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc8bd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc8bd-109">Remarks</span></span>  
 <span data-ttu-id="fc8bd-110">O valor referenciado pelo `pdwMachine` parâmetro pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="fc8bd-111">Valor</span><span class="sxs-lookup"><span data-stu-id="fc8bd-111">Value</span></span>|<span data-ttu-id="fc8bd-112">Arquitetura do computador</span><span class="sxs-lookup"><span data-stu-id="fc8bd-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="fc8bd-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="fc8bd-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="fc8bd-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="fc8bd-114">0x014C</span></span>|<span data-ttu-id="fc8bd-115">x86</span><span class="sxs-lookup"><span data-stu-id="fc8bd-115">x86</span></span>|  
|<span data-ttu-id="fc8bd-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="fc8bd-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="fc8bd-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="fc8bd-117">0x0200</span></span>|<span data-ttu-id="fc8bd-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="fc8bd-118">Intel IPF</span></span>|  
|<span data-ttu-id="fc8bd-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="fc8bd-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="fc8bd-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="fc8bd-120">0x8664</span></span>|<span data-ttu-id="fc8bd-121">X64</span><span class="sxs-lookup"><span data-stu-id="fc8bd-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc8bd-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc8bd-122">Requirements</span></span>  
 <span data-ttu-id="fc8bd-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc8bd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8bd-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc8bd-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc8bd-125">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fc8bd-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8bd-126">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8bd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8bd-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc8bd-127">See Also</span></span>  
 [<span data-ttu-id="fc8bd-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fc8bd-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="fc8bd-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fc8bd-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fc8bd-130">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="fc8bd-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
