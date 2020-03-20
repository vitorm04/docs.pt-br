---
title: Método ExportNestedType
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179410"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="5c990-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="5c990-102">ExportNestedType Method</span></span>
<span data-ttu-id="5c990-103">Especifica tipos aninhados como exportáveis.</span><span class="sxs-lookup"><span data-stu-id="5c990-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="5c990-104">O [Método ExportarTipo](exporttype-method.md) também pode exportar tipos aninhados, mas este método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="5c990-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c990-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c990-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="5c990-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c990-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5c990-107">ID de montagem para exportação.</span><span class="sxs-lookup"><span data-stu-id="5c990-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5c990-108">Token de arquivo ou montagem de arquivo que define o tipo a ser exportável.</span><span class="sxs-lookup"><span data-stu-id="5c990-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="5c990-109">Digite o tipo de tipo a ser exportável.</span><span class="sxs-lookup"><span data-stu-id="5c990-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="5c990-110">Símbolo do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="5c990-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="5c990-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="5c990-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5c990-112">`ComType`bandeiras `tdPublic` como `tdNested`ou .</span><span class="sxs-lookup"><span data-stu-id="5c990-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="5c990-113">Esse valor pode ser passado para [o método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c990-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="5c990-114">Recebe token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="5c990-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c990-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5c990-115">Return Value</span></span>  
 <span data-ttu-id="5c990-116">Retorna S_OK se o método for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="5c990-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c990-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c990-117">Requirements</span></span>  
 <span data-ttu-id="5c990-118">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="5c990-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c990-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c990-119">See also</span></span>

- [<span data-ttu-id="5c990-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="5c990-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5c990-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="5c990-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5c990-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="5c990-122">ALink API</span></span>](index.md)
