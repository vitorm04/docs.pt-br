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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007384"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="6043f-102">Enumeração CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="6043f-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="6043f-103">Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o método [IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6043f-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6043f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6043f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="6043f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6043f-105">Members</span></span>  
  
|<span data-ttu-id="6043f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6043f-106">Member</span></span>|<span data-ttu-id="6043f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6043f-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="6043f-108">O arquivo é mapeado como um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="6043f-108">The file is mapped as a data file.</span></span> <span data-ttu-id="6043f-109">Ou seja, o `SEC_IMAGE` sinalizador não foi passado para a função Microsoft Win32 `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="6043f-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="6043f-110">O arquivo é mapeado para execução, usando a `LoadLibrary` função ou a `CreateFileMapping` função com o `SEC_IMAGE` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="6043f-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6043f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6043f-111">Requirements</span></span>  
 <span data-ttu-id="6043f-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6043f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6043f-113">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="6043f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6043f-114">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6043f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6043f-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="6043f-115">See also</span></span>

- [<span data-ttu-id="6043f-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="6043f-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="6043f-117">Método GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="6043f-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
