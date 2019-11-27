---
title: Enumeração CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450301"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="e4170-102">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="e4170-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="e4170-103">Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o método [IMetaDataInfo:: GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e4170-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4170-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4170-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="e4170-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e4170-105">Members</span></span>  
  
|<span data-ttu-id="e4170-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4170-106">Member</span></span>|<span data-ttu-id="e4170-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4170-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="e4170-108">O arquivo é mapeado como um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="e4170-108">The file is mapped as a data file.</span></span> <span data-ttu-id="e4170-109">Ou seja, o sinalizador `SEC_IMAGE` não foi passado para a função de `CreateFileMapping` do Microsoft Win32.</span><span class="sxs-lookup"><span data-stu-id="e4170-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="e4170-110">O arquivo é mapeado para execução, usando a função `LoadLibrary` ou a função `CreateFileMapping` com o sinalizador `SEC_IMAGE`.</span><span class="sxs-lookup"><span data-stu-id="e4170-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4170-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4170-111">Requirements</span></span>  
 <span data-ttu-id="e4170-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4170-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4170-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e4170-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e4170-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4170-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4170-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4170-115">See also</span></span>

- [<span data-ttu-id="e4170-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e4170-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="e4170-117">Método GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="e4170-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
