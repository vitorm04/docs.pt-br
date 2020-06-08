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
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490426"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="4d90d-102">Método IMetaDataImport2::GetPEKind</span><span class="sxs-lookup"><span data-stu-id="4d90d-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="4d90d-103">Obtém um valor que identifica a natureza do código no arquivo executável portátil (PE), normalmente um arquivo DLL ou EXE, que é definido no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="4d90d-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d90d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d90d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d90d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d90d-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="4d90d-106">fora Um ponteiro para um valor da enumeração [CorPEKind](corpekind-enumeration.md) que descreve o arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="4d90d-106">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="4d90d-107">fora Um ponteiro para um valor que identifica a arquitetura do computador.</span><span class="sxs-lookup"><span data-stu-id="4d90d-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="4d90d-108">Consulte a próxima seção para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="4d90d-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d90d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d90d-109">Remarks</span></span>  
 <span data-ttu-id="4d90d-110">O valor referenciado pelo `pdwMachine` parâmetro pode ser um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="4d90d-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="4d90d-111">Valor</span><span class="sxs-lookup"><span data-stu-id="4d90d-111">Value</span></span>|<span data-ttu-id="4d90d-112">Arquitetura do computador</span><span class="sxs-lookup"><span data-stu-id="4d90d-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="4d90d-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="4d90d-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="4d90d-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="4d90d-114">0x014C</span></span>|<span data-ttu-id="4d90d-115">x86</span><span class="sxs-lookup"><span data-stu-id="4d90d-115">x86</span></span>|  
|<span data-ttu-id="4d90d-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="4d90d-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="4d90d-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="4d90d-117">0x0200</span></span>|<span data-ttu-id="4d90d-118">IPF Intel</span><span class="sxs-lookup"><span data-stu-id="4d90d-118">Intel IPF</span></span>|  
|<span data-ttu-id="4d90d-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="4d90d-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="4d90d-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="4d90d-120">0x8664</span></span>|<span data-ttu-id="4d90d-121">x64</span><span class="sxs-lookup"><span data-stu-id="4d90d-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d90d-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d90d-122">Requirements</span></span>  
 <span data-ttu-id="4d90d-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d90d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d90d-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4d90d-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d90d-125">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d90d-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d90d-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d90d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d90d-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d90d-127">See also</span></span>

- [<span data-ttu-id="4d90d-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4d90d-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="4d90d-129">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4d90d-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4d90d-130">Enumeração CorPEKind</span><span class="sxs-lookup"><span data-stu-id="4d90d-130">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
