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
ms.openlocfilehash: a3056836d289383161f9fa538c3c6349f88b6ba6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905730"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="3ea16-102">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="3ea16-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="3ea16-103">Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o [imetadatainfo:: Getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3ea16-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ea16-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="3ea16-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3ea16-105">Members</span></span>  
  
|<span data-ttu-id="3ea16-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3ea16-106">Member</span></span>|<span data-ttu-id="3ea16-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ea16-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="3ea16-108">O arquivo é mapeado como um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="3ea16-108">The file is mapped as a data file.</span></span> <span data-ttu-id="3ea16-109">Ou seja, o `SEC_IMAGE` sinalizador não foi passado para o Microsoft Win32 `CreateFileMapping` função.</span><span class="sxs-lookup"><span data-stu-id="3ea16-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="3ea16-110">O arquivo é mapeado para a execução, usando o `LoadLibrary` função ou o `CreateFileMapping` funcionar com o `SEC_IMAGE` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="3ea16-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ea16-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ea16-111">Requirements</span></span>  
 <span data-ttu-id="3ea16-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea16-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea16-113">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3ea16-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3ea16-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea16-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea16-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ea16-115">See also</span></span>

- [<span data-ttu-id="3ea16-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3ea16-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="3ea16-117">Método GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="3ea16-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
