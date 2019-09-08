---
title: Método SetManifestFile
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787202"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="268c6-102">Método SetManifestFile</span><span class="sxs-lookup"><span data-stu-id="268c6-102">SetManifestFile Method</span></span>
<span data-ttu-id="268c6-103">Permite que você especifique ou redefina o arquivo de manifesto que o vinculador usa ao criar o assembly.</span><span class="sxs-lookup"><span data-stu-id="268c6-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="268c6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="268c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="268c6-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="268c6-106">O nome do arquivo de manifesto cujo conteúdo é colocado no blob de recursos do Win32.</span><span class="sxs-lookup"><span data-stu-id="268c6-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="268c6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="268c6-107">Return Value</span></span>  
 <span data-ttu-id="268c6-108">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="268c6-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="268c6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="268c6-109">Remarks</span></span>  
 <span data-ttu-id="268c6-110">Chame isso antes de solicitar o Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="268c6-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="268c6-111">O valor do `pszFile` parâmetro é o nome do arquivo de manifesto cujo conteúdo é lido e colocado nos recursos do Win32 com a ID de RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="268c6-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="268c6-112">Quando chamado usando um parâmetro de NULL, qualquer manifesto lido anteriormente é limpo.</span><span class="sxs-lookup"><span data-stu-id="268c6-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="268c6-113">Isso permite que um redefina o estado do vinculador para o tempo de inicialização.</span><span class="sxs-lookup"><span data-stu-id="268c6-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="268c6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="268c6-114">Requirements</span></span>  
 <span data-ttu-id="268c6-115">Requer aLink. h</span><span class="sxs-lookup"><span data-stu-id="268c6-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268c6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="268c6-116">See also</span></span>

- [<span data-ttu-id="268c6-117">Interface IALink3</span><span class="sxs-lookup"><span data-stu-id="268c6-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="268c6-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="268c6-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="268c6-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="268c6-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="268c6-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="268c6-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
