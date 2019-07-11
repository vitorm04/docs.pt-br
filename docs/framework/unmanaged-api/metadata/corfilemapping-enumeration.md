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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 719f0522cc43625a4d6cc8afa838d869e47b40d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781844"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="af3a7-102">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="af3a7-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="af3a7-103">Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o [imetadatainfo:: Getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="af3a7-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af3a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af3a7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="af3a7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="af3a7-105">Members</span></span>  
  
|<span data-ttu-id="af3a7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="af3a7-106">Member</span></span>|<span data-ttu-id="af3a7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="af3a7-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="af3a7-108">O arquivo é mapeado como um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="af3a7-108">The file is mapped as a data file.</span></span> <span data-ttu-id="af3a7-109">Ou seja, o `SEC_IMAGE` sinalizador não foi passado para o Microsoft Win32 `CreateFileMapping` função.</span><span class="sxs-lookup"><span data-stu-id="af3a7-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="af3a7-110">O arquivo é mapeado para a execução, usando o `LoadLibrary` função ou o `CreateFileMapping` funcionar com o `SEC_IMAGE` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="af3a7-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af3a7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af3a7-111">Requirements</span></span>  
 <span data-ttu-id="af3a7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af3a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af3a7-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="af3a7-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="af3a7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af3a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af3a7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af3a7-115">See also</span></span>

- [<span data-ttu-id="af3a7-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="af3a7-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="af3a7-117">Método GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="af3a7-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
